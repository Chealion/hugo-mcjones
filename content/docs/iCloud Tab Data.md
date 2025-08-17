
---
title: "iCloud Tab Data"
date: 2025-06-16T14:47:38Z
lastmod: 2025-06-16T15:08:59Z
categories: ['snippet']
draft: false
---


# iCloud Tab Data

Your iCloud shared tab data is saved in a sqlite database on your computer.

While it used to live in `~/Library/Safari/CloudTabs.db`, it now lives at `~/Library/Containers/com.apple.Safari/Data/Library/Safari/CloudTabs.db` (a lot of things have moved to `~/Library/Containers` over the years to wall them off from the rest of the system without permission)

## All the Tabs One Liner
```
sqlite3 ~/Library/Containers/com.apple.Safari/Data/Library/Safari/CloudTabs.db 'select url from cloud_tabs'
```

<!-- #snippet #public -->

<!-- {BearID:41ACBF90-0162-4B6B-BE3F-3A49526D726E} -->
