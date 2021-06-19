---
title: curl (devhints)
category: cli
tags: [curl,netowrk,rest]
---

## Options

### Options

```sh
-o <file>    # --output: write to file
-u user:pass # --user: Authentication
```

```sh
-v           # --verbose
-vv          # Even more verbose
-s           # --silent
```

```sh
-i           # --include: Include the HTTP-header in the output
-I           # --head: headers only
```

### Request

```sh
-X POST          # --request
-L               # follow link if page redirects
```

### Data

```sh
-d 'data'    # --data: HTTP post data, URL encoded (eg, status="Hello")
-d @file     # --data via file
-G           # --get: send -d data via get
```

### Headers

```sh
-A <str>         # --user-agent
-b name=val      # --cookie
-b FILE          # --cookie
-H "X-Foo: y"    # --header
--compressed     # use deflate/gzip
```

### SSL

```sh
    --cacert <file>
    --capath <dir>
```

```sh
-E, --cert <cert>     # --cert: Client cert file
    --cert-type       # der/pem/eng
-k, --insecure        # for self-signed certs
```

## Examples

```sh
# Post data:
curl -d password=x http://x.com/y
```

```sh
# Auth/data:
curl -u user:pass -d status="Hello" http://twitter.com/statuses/update.xml
```

```sh
# multipart file upload
curl -v -include --form key1=value1 --form upload=@localfilename URL
```

```sh
# Use Curl to Check if a remote resource is available
curl -o /dev/null --silent -Iw "%{http_code}" https://example.com/my.remote.tarball.gz ```
