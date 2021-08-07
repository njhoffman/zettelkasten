---
title: Bash functions (devhints)
category: lang
source: devhints
tags: [bash,functions]
---

### Defining functions

```sh
myfunc() {
    echo "hello $1"
}
```

```sh
# Same as above (alternate syntax)
function myfunc() {
    echo "hello $1"
}
```

```sh
myfunc "John"
```

### Returning values

```sh
myfunc() {
    local myresult='some value'
    echo $myresult
}
```

```sh
result="$(myfunc)"
```

### Raising errors

```sh
myfunc() {
  return 1
}
```

```sh
if myfunc; then
  echo "success"
else
  echo "failure"
fi
```

### Arguments

| Expression | Description                                      |
| ---        | ---                                              |
| `$#`       | Number of arguments                              |
| `$*`       | All postional arguments  (as a single word)     |
| `$@`       | All postitional arguments (as separate strings)  |
| `$1`       | First argument                                   |
| `$_`       | Last argument of the previous command            |

**Note**: `$@` and `$*` must be quoted in order to perform as described.
Otherwise, they do exactly the same thing (arguments as separate strings).
