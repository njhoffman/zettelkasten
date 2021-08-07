---
title: sed [devh]
tags: [devhints,formatting]
---

### In-place replacement
```sh
sed -i -e 's/foo/bar/' example.md
```

## File regions
{:.-three-column}

### Print until a certain line is met
```sh
sed '/begin api/q'
```

### Print until a certain line is met, but not that line
```sh
sed '/^# begin/,$d'
```

### Print everything after a given line
```sh
sed -n '/end api/,$p'
```

### Print everything except matching
```sh
sed -n '/regex/d;'
```
Print everything except lines matching regex. Useful for printing files with comments.

___


#### **See also...**

* [[sed.tldr]]
