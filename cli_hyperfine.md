---
title: hyperfine - a command line benchmarking tool
tags: [cli, profiling, performance]
---

## Hyperfine: a command line benchmarking tool

```sh
  hyperfine --warmup 3 'fd -e jpg -uu' 'find iname "*.jpg"'
  hyperfine --min-runs 5 'sleep 0.2' 'sleep 3.2' --export-markdown
  # --export-markdown, --export-csv, --export-json, --export-asciidoc
```
*Use `--prepare` argument to run special command before each run*
```sh
  # gain temporary permission and clear hard disk caches before each run
  sudo -v
  hyperfine --prepare 'sync; echo 3 | sudo tee /proc/sys/vm/drop_caches' 'grep -R TODO *'
```
*Use `--parameter-scan` to vary a single parameter with the same command*
```sh
  hyperfine --prepare 'make clean' --parameter-scan num_threads 1 12 'make -j {num_threads}'
  hyperfine --parameter-scan delay 0.3 0.7 -D 0.2 'sleep {delay}'
```
Shell functions need to be exported or assigned to separate files
```sh
  export -f my_shell_function
  echo 'my_function() { sleep 1 }' > /tmp/my_function.sh
  echo 'alias my_alias="sleep 1"' > /tmp/my_alias.sh
  hyperfine 'source /tmp/my_function.sh; eval my_function'
  hyperfine 'source /tmp/my_alias.sh; eval my_alias'

  # intallation
  wget https://github.com/sharkdp/hyperfine/releases/download/v1.11.0/hyperfine_1.11.0_amd64.deb && \
    sudo dpkg -i hyperfine_1.11.0_amd64.deb
  cargo/brew install hyperfine
```
