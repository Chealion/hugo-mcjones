
---
title: "sqlite3 Frequent Commands"
date: 2025-11-16T17:04:17Z
lastmod: 2025-11-16T17:08:06Z
categories: ['snippet', 'sqlite']
draft: false
---


# sqlite3 Frequent Commands
## Tables and Schema
```
.tables
.schema user
```

## Pretty Print / Columns / Headers
Column mode turns on columns all on it’s own.
```
.headers on

ward_id|ward_num
1|6

.mode column
ward_id  ward_num
-------  --------
1        6

.width 10 10
ward_id     ward_num
----------  ----------
1           6
```

<!-- #public #snippet #sqlite -->

<!-- {BearID:C3517FFD-E0BE-47B5-A3C5-5D39C9D29A1C} -->
