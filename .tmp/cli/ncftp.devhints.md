---
title: ncftp (devhints)
category: cli
tags: [ncftp,network]
---

### Bookmarking

```sh
$ ncftp
$ open -u username ftp.host.com
$ bookmark bookmarkname
```

### Mass download

```sh
$ ncftpget -R bookmarkname /www/ .
```

### Mass upload

```sh
$ ncftpput -R bookmarkname /www/ .
```

### Upload just the changed files

```sh
$ git show --pretty="format:" --name-only HEAD~1
$ ncftpget -R -C log bookmarkname /www/ .
```
