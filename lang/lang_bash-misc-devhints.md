---
title: (lang) Bash miscellaneous [devhints]
tags: [lang,devhints,bash,trap,redirection,subshells,switch,heredoc]
---

### Numeric calculations

```sh
$((a + 200))      # Add 200 to $a
$(($RANDOM%200))  # Random number 0..199
```

### Subshells

```sh
(cd somedir; echo "I'm now in $PWD")
pwd # still in first directory
```

### Redirection

```sh
python hello.py > output.txt   # stdout to (file)
python hello.py >> output.txt  # stdout to (file), append
python hello.py 2> error.log   # stderr to (file)
python hello.py 2>&1           # stderr to stdout
python hello.py 2>/dev/null    # stderr to (null)
python hello.py &>/dev/null    # stdout and stderr to (null)
python hello.py < foo.txt      # feed foo.txt to stdin for python
```

### Inspecting commands

```sh
command -V cd
#=> "cd is a function/alias/whatever"
```

### Trap errors

```sh
trap 'echo Error at about $LINENO' ERR
```

or

```sh
traperr() {
  echo "ERROR: ${BASH_SOURCE[1]} at about ${BASH_LINENO[0]}"
}

set -o errtrace
trap traperr ERR
```

### Case/switch

```sh
case "$1" in
  start | up)
    vagrant up
    ;;

  *)
    echo "Usage: $0 {start|stop|ssh}"
    ;;
esac
```

### Source relative

```sh
source "${0%/*}/../share/foo.sh"
```

### printf

```sh
printf "Hello %s, I'm %s" Sven Olga
#=> "Hello Sven, I'm Olga

printf "1 + 1 = %d" 2
#=> "1 + 1 = 2"

printf "This is how you print a float: %f" 2
#=> "This is how you print a float: 2.000000"
```

### Directory of script

```sh
DIR="${0%/*}"
```

### Getting options

```sh
while [[ "$1" =~ ^- && ! "$1" == "--" ]]; do case $1 in
  -V | --version )
    echo $version
    exit
    ;;
  -s | --string )
    shift; string=$1
    ;;
  -f | --flag )
    flag=1
    ;;
esac; shift; done
if [[ "$1" == '--' ]]; then shift; fi
```

### Heredoc

```sh
cat <<END
hello world
END
```

### Reading input

```sh
echo -n "Proceed? [y/n]: "
read ans
echo $ans
```

```sh
read -n 1 ans    # Just one character
```

### Special variables

| Expression | Description                  |
| ---------- | ---------------------------- |
| `$?`       | Exit status of last task     |
| `$!`       | PID of last background task  |
| `$$`       | PID of shell                 |
| `$0`       | Filename of the shell script |


### Go to previous directory

```sh
pwd # /home/user/foo
cd bar/
pwd # /home/user/foo/bar
cd -
pwd # /home/user/foo
```

### Check for command's result

```sh
if ping -c 1 google.com; then
  echo "It appears you have a working internet connection"
fi
```

### Grep check

```sh
if grep -q 'foo' ~/.bash_history; then
  echo "You appear to have typed 'foo' in the past"
fi
