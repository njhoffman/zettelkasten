---
title: rsync (devhints)
category: CLI
tags: [rsync,network,files]
---

### Basic example

```sh
# syncing folder src into dest:
rsync -avz ./src /dest
# syncing the content of src into dest:
rsync -avz ./src/ /dest
```

### OSX

```sh
--exclude '.Trashes'
--exclude '.Spotlight-V100'
--exclude '.fseventsd'
```

### Transfer options

```sh
-z, --compress
-n, --dry-run
    --partial   # allows resuming of aborted syncs
    --bwlimit=RATE    # limit socket I/O bandwidth
```

### Display options

```sh
-q, --quiet
-v, --verbose
    --stats
-h, --human-readable
    --progress
-P                     # same as --partial --progress
```

### Skipping options

```sh
-u, --update     # skip files newer on dest
-c, --checksum   # skip based on checksum, not mod-time & size
```

### Backup options

```sh
-b, --backup           # backup with suffix
    --suffix=SUFFIX    # default ~ without --backup-dir
    --backup-dir=DIR
```

### Include options

```sh
--exclude=PATTERN
--include=PATTERN
```

```sh
--exclude-from=FILE
--include-from=FILE
--files-from=FILE    # read list of filenames from FILE
```

```sh
-C, --cvs-exclude    # exclude from local/global .cvsignore
```

### Archive options

```sh
-a, --archive    # archive (-rlptgoD)
```

```sh
-r, --recursive
-l, --links      # copy symlinks as links
-p, --perms      # preserve permissions
-t, --times      # preserve times
-g, --group      # preserve group
-o, --owner      # preserve owner
-D               # same as --devices --specials
```

```sh
--delete         # Delete extra files
```
