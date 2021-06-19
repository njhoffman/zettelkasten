---
title: Bash loops (devhints)
category: lang
source: devhints
tags: [bash,loops]
---

### Basic for loop

```sh
for i in /etc/rc.*; do
  echo $i
done
```

### C-like for loop

```sh
for ((i = 0 ; i < 100 ; i++)); do
  echo $i
done
```

### Ranges

```sh
for i in {1..5}; do
    echo "Welcome $i"
done
```

#### With step size

```sh
for i in {5..50..5}; do
    echo "Welcome $i"
done
```

### Reading lines

```sh
cat file.txt | while read line; do
  echo $line
done
```

### Forever

```sh
while true; do
  ···
done
```
