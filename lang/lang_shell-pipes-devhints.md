---
title: "(lang) shell: named pipes [devhints]"
tags: [lang,devhints,pipes, redirection]
---

### Named pipes

```sh
diff <(ls ./old) <(ls ./new)
```

This creates a virtual file with the contents of the output of `ls ./old`.
