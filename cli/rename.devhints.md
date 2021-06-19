---
title: rename (devhints)
category: cli
tags: [rename,files]
---

### Installation

```sh
brew install rename
```

### Regex substitution

```sh
rename 's/hello/world/' *.txt
```

Rename `hello.txt` to `world.txt` and so on in `*.txt`.

### Replace extension

```sh
rename -s .png .jpg.png *.png
```

Replace `.png` with `.jpg.png` in `*.png`.

### Options

| Option | Description               |
| ---    | ---                       |
| `-n`   | Simulation                |
| `-l`   | Symlink instead of rename |
| `-i`   | Interactive               |

## Also see

- [Rename website](http://plasmasturm.org/code/rename/) _(plasmasturm.org)_
