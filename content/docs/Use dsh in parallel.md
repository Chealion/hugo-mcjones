
---
title: "Use dsh in parallel"
date: 2022-07-05T01:34:05Z
lastmod: 2025-04-01T20:16:05Z
categories: ['snippet', 'dsh']
draft: false
---


# Use dsh in parallel
Use `-c` for all at once

Or `-F X` for a certain number at a time

```
dsh -Mg containers -F 5 whoami
```

<!-- #public #snippet #dsh -->

<!-- {BearID:1318DF0B-B992-4C6E-BC4D-2F7D574A5A4F-1190-00000AE66BAC8E29} -->
