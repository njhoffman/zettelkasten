TL;DR: exportable arrays are not directly supported up to and including bash-5.1, but you can (effectively) export arrays in one of two ways:
a simple modification to the way the child scripts are invoked
use an exported function to store the array initialisation, with a simple modification to the child scripts

The first thing to understand is that the bash environment (more properly command execution environment) is different to the POSIX concept of an environment. The POSIX environment is a collection of un-typed name=value pairs, and can be passed from a process to its children in various ways (effectively a limited form of IPC).
The bash execution environment is effectively a superset of this, with typed variables, read-only and exportable flags, arrays, functions and more. This partly explains why the output of set (bash builtin) and env or printenv differ.
When you invoke another bash shell you're starting a new process, you loose some bash state. However, if you dot-source a script, the script is run in the same environment; or if you run a subshell via ( ) the environment is also preserved (because bash forks, preserving its complete state, rather than reinitialising using the process environment).
The limitation referenced in @lesmana's answer arises because the POSIX environment is simply name=value pairs with no extra meaning, so there's no agreed way to encode or format typed variables, see below for an interesting bash quirk regarding functions , and an upcoming change in bash-4.3(proposed array feature abandoned).
There are a couple of simple ways to do this using declare -p (built-in) to output some of the bash environment as a set of one or more declare statements which can be used reconstruct the type and value of a "name". This is basic serialisation, but with rather less of the complexity some of the other answers imply. declare -p preserves array indexes, sparse arrays and quoting of troublesome values. For simple serialisation of an array you could just dump the values line by line, and use read -a myarray to restore it (works with contiguous 0-indexed arrays, since read -a automatically assigns indexes).
These methods do not require any modification of the script(s) you are passing the arrays to.

```bash
  declare -p array1 array2 > .bash_arrays       # serialise to an intermediate file
  bash -c ". .bash_arrays; . otherscript.sh"    # source both in the same environment
  Variations on the above bash -c "..." form are sometimes (mis-)used in crontabs to set variables.
  # Alternatives include:
  declare -p array1 array2 > .bash_arrays       # serialise to an intermediate file
  BASH_ENV=.bash_arrays otherscript.sh          # non-interactive startup script
  # Or, as a one-liner:
  BASH_ENV=<(declare -p array1 array2) otherscript.sh
```

The last one uses process substitution to pass the output of the declare command as an rc script. (This method only works in bash-4.0 or later: earlier versions unconditionally fstat() rc files and use the size returned to read() the file in one go; a FIFO returns a size of 0, and so won't work as hoped.)
In a non-interactive shell (i.e. shell script) the file pointed to by the BASH_ENV variable is automatically sourced. You must make sure bash is correctly invoked, possibly using a shebang to invoke "bash" explicitly, and not #!/bin/sh as bash will not honour BASH_ENV when in historical/POSIX mode.
If all your array names happen to have a common prefix you can use `declare -p ${!myprefix*}` to expand a list of them, instead of enumerating them.
You probably should not attempt to export and re-import the entire bash environment using this method, some special bash variables and arrays are read-only, and there can be other side-effects when modifying special variables.
(You could also do something slightly disagreeable by serialising the array definition to an exportable variable, and using eval, but let's not encourage the use of eval ...

```bash
  $ array=([1]=a [10]="b c")
  $ export scalar_array=$(declare -p array)
  $ bash # start a new shell
  $ eval $scalar_array
  $ declare -p array
  declare -a array='([1]="a" [10]="b c")'
  )

# As referenced above, there's an interesting quirk: special support for exporting functions through the environment:

  function myfoo() {
      echo foo
  }
#  with export -f or set +a to enable this behaviour, will result in this in the (process) environment, visible with printenv:
  myfoo=() { echo foo }
```

The variable is functionname (or functioname() for backward compatibility) and its value is () { functionbody }.
When a subsequent bash process starts it will recreate a function from each such environment variable. If you peek into the bash-4.2 source file variables.c you'll see variables starting with () { are handled specially.
(Though creating a function using this syntax with declare -f is forbidden.)
Update: The "shellshock" security issue is related to this feature, contemporary systems may disable automatic function import from the environment as a mitigation.
If you keep reading though, you'll see an #if 0 (or #if ARRAY_EXPORT) guarding code that checks variables starting with `([` and ending with `)`, and a comment stating "Array variables may not yet be exported".
The good news is that in the current development version bash-4.3rc2 the ability to export indexed arrays (not associative) is enabled. This feature is not likely to be enabled, as noted above.
We can use this to create a function which restores any array data required:

```bash
  % function sharearray() {
      array1=(a b c d)
  }
  % export -f sharearray
  % bash -c 'sharearray; echo ${array1[*]}'
  # So, similar to the previous approach, invoke the child script with:
  bash -c "sharearray; . otherscript.sh"

  # Or, you can conditionally invoke the sharearray function in the child script by adding at some appropriate point:
  declare -F sharearray >/dev/null && sharearray
```


Note there is no declare -a in the sharearray function, if you do that the array is implicitly local to the function, not what is wanted.
bash-4.2 supports declare -g that makes a variable declared in a function into a global, so declare -ga can then be used.
(Since associative arrays require a declare -A you won't be able to use this method for global associative arrays prior to bash-4.2, from v4.2 declare -Ag will work as hoped.)
The GNU parallel documentation has useful variation on this method, see the discussion of --env in the man page.
Your question as phrased also indicates you may be having problems with export itself. You can export a name after you've created or modified it. "exportable" is a flag or property of a variable, for convenience you can also set and export in a single statement. Up to bash-4.2 export expects only a name, either a simple (scalar) variable or function name are supported.
Even if you could (in future) export arrays, exporting selected indexes (a slice) may not be supported (though since arrays are sparse there's no reason it could not be allowed). Though bash also supports the syntax declare -a name[0], the subscript is ignored, and "name" is simply a normal indexed array.
