---
title: Bash introduction (devhints)
category: lang
source: devhints
tags: [bash,intro]
---

### Introduction

This is a quick reference to getting started with Bash scripting.

- [Learn bash in y minutes](https://learnxinyminutes.com/docs/bash/) _(learnxinyminutes.com)_
- [Bash Guide](http://mywiki.wooledge.org/BashGuide) _(mywiki.wooledge.org)_

### Example

```sh
#!/usr/bin/env bash

NAME="John"
echo "Hello $NAME!"
```

### Variables

```sh
NAME="John"
echo $NAME
echo "$NAME"
echo "${NAME}!"
```

### String quotes

```sh
NAME="John"
echo "Hi $NAME"  #=> Hi John
echo 'Hi $NAME'  #=> Hi $NAME
```

### Shell execution

```sh
echo "I'm in $(pwd)"
echo "I'm in `pwd`"
# Same
```


### Conditional execution

```sh
git commit && git push
git commit || echo "Commit failed"
```

### Functions
{: id='functions-example'}

```sh
get_name() {
  echo "John"
}

echo "You are $(get_name)"
```


### Conditionals
{: id='conditionals-example'}

```sh
if [[ -z "$string" ]]; then
  echo "String is empty"
elif [[ -n "$string" ]]; then
  echo "String is not empty"
fi
```


### Strict mode

```sh
set -euo pipefail
IFS=$'\n\t'
```


### Brace expansion

```sh
echo {A,B}.js
```

| Expression | Description         |
| ---------- | ------------------- |
| `{A,B}`    | Same as `A B`       |
| `{A,B}.js` | Same as `A.js B.js` |
| `{1..5}`   | Same as `1 2 3 4 5` |
