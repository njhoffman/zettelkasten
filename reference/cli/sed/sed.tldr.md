---
title: sed [tldr]
tags: [formatting, tldr]
---

> Edit text in a scriptable manner.

- Replace the first occurrence of a regular expression in each line of a file, and print the result:

```sh
sed 's/{{regex}}/{{replace}}/' {{filename}}
```

- Replace all occurrences of an extended regular expression in a file, and print the result:

```sh
sed -r 's/{{regex}}/{{replace}}/g' {{filename}}
```

- Replace all occurrences of a string in a file, overwriting the file (i.e. in-place):

```sh
sed -i 's/{{find}}/{{replace}}/g' {{filename}}
```

- Replace only on lines matching the line pattern:

```sh
sed '/{{line_pattern}}/s/{{find}}/{{replace}}/' {{filename}}
```

- Delete lines matching the line pattern:

```sh
sed '/{{line_pattern}}/d' {{filename}}
```

- Print the first 11 lines of a file:

```sh
sed 11q {{filename}}
```

- Apply multiple find-replace expressions to a file:

```sh
sed -e 's/{{find}}/{{replace}}/' -e 's/{{find}}/{{replace}}/' {{filename}}
```

- Replace separator `/` by any other character not used in the find or replace patterns, e.g., `#`:

```sh
sed 's#{{find}}#{{replace}}#' {{filename}}
```

___


#### **See also...**

* [[sed.devh]]
