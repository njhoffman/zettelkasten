---
title: find (devhints)
category: cli
tags: [find,files]
---

### Usage

```sh
find <path> <conditions> <actions>
```

### Conditions

```sh
-name "*.c"
```

```sh
-user jonathan
-nouser
```

```sh
-type f            # File
-type d            # Directory
-type l            # Symlink
```

```sh
-depth 2           # At least 3 levels deep
-regex PATTERN
```

```sh
-size 8            # Exactly 8 512-bit blocks
-size -128c        # Smaller than 128 bytes
-size 1440k        # Exactly 1440KiB
-size +10M         # Larger than 10MiB
-size +2G          # Larger than 2GiB
```

```sh
-newer   file.txt
-newerm  file.txt        # modified newer than file.txt
-newerX  file.txt        # [c]hange, [m]odified, [B]create
-newerXt "1 hour ago"    # [t]imestamp
```

### Access time conditions

```sh
-atime 0           # Last accessed between now and 24 hours ago
-atime +0          # Accessed more than 24 hours ago
-atime 1           # Accessed between 24 and 48 hours ago
-atime +1          # Accessed more than 48 hours ago
-atime -1          # Accessed less than 24 hours ago (same a 0)
-ctime -6h30m      # File status changed within the last 6 hours and 30 minutes
-mtime +1w         # Last modified more than 1 week ago
```

These conditions only work in MacOS and BSD-like systems (no GNU/Linux support).

### Condition flow

```sh
\! -name "*.c"
\( x -or y \)
```

### Actions

```sh
-exec rm {} \;
-print
-delete
```

### Examples

```sh
find . -name '*.jpg'
find . -name '*.jpg' -exec rm {} \;
```

```sh
find . -newerBt "24 hours ago"
```

```sh
find . -type f -mtime +29 # find files modified more than 30 days ago
```
