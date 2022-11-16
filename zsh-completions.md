---
title: ZSH Completions
---

## Looking up zsh completion definitions

```bash
# The name of the completion function for the command foo is:
$_comps[foo].
# To see the code of a function myfunc, run
echo -E $functions[myfunc]
# or just
echo $functions[myfunc]
# if you have the bsd_echo option on, or
print -rl $functions[myfunc]
# So to see the code of the completion function for the command foo, run
echo -E $functions[$_comps[foo]]
# If the function name has no alias, run
which $_comps[foo]
# This shows the code without comments (and with normalized whitespace: it's a human-readable dump of the bytecode that zsh stores internally). If you want to see the original file defined in the code, run whence -v $_comps[foo] or echo $functions_source[$_comps[foo]]. The functions_source array is only available if the module zsh/parameter is loaded (you can do this with zmodload zsh/parameter) and only since zsh 5.4.
# If you haven't used the function yet, you'll see something like builtin autoload -XU instead of the code, and no path to the source.
# To see the path to the source, run
autoload -r $_comps[foo]
# first to make zsh resolve the path to the source,
# then you can display it with which or whence or $functions_source.
zmodload zsh/parameter
(($+_comps[foo])) &&
autoload -r $_comps[foo] &&
((+$functions_source[$_comps[foo]])) &&
cat $functions_source[$_comps[foo]]
```
