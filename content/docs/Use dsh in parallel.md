
---
title: Use dsh in parallel
date: 2022-07-04 19:34:05
lastmod: 2022-07-17 10:41:11
categories: ['snippet', 'dsh']
draft: false
---


# Use dsh in parallel
Use `-c` for all at once

Or `-f X` for a certain number at a time

```
dsh -Mg containers -f 5 whoami
```

<!-- #public #snippet #dsh -->

<!-- {BearID:1318DF0B-B992-4C6E-BC4D-2F7D574A5A4F-1190-00000AE66BAC8E29} -->
