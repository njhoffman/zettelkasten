---
title: (cli) cron [devhints]
tags: [cli,devhints,cron,scheduling]
---

## Format

### Format

```
Min  Hour Day  Mon  Weekday
```

```
*    *    *    *    *  command to be executed
```

```
┬    ┬    ┬    ┬    ┬
│    │    │    │    └─  Weekday  (0=Sun .. 6=Sat)
│    │    │    └──────  Month    (1..12)
│    │    └───────────  Day      (1..31)
│    └────────────────  Hour     (0..23)
└─────────────────────  Minute   (0..59)
```

### Examples

| Example        | Description           |
| ---            | ---                   |
| `0 * * * *`    | every hour            |
| `*/15 * * * *` | every 15 mins         |
| `0 */2 * * *`  | every 2 hours         |
| `0 0 * * 0`    | every Sunday midnight |
| ---            | ---                   |
| `@reboot`      | every reboot          |

### Crontab

```sh
# Adding tasks easily
echo "@reboot echo hi" | crontab
```

```sh
# Open in editor
crontab -e
```

```sh
# List tasks
crontab -l [-u user]
```
