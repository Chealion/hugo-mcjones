
---
title: "SQL on a CSV file using sqlite"
date: 2022-06-21T16:15:19Z
lastmod: 2022-07-17T16:43:14Z
categories: ['snippet', 'sqlite']
draft: false
---


# SQL on a CSV file using sqlite
Using sqlite’s in memory database to load a .csv called taxi.csv

```
sqlite3 :memory: -cmd '.mode csv' -cmd '.import taxi.csv taxi' \
  'SELECT passenger_count, COUNT(*), AVG(total_amount) FROM taxi GROUP BY passenger_count'
```

Source: https://til.simonwillison.net/sqlite/one-line-csv-operations

This was found for doing some work to benchmark dsq - a tool for querying against a multitude of format types (JSON, CSV, Excel, Parquet, etc.) - https://github.com/multiprocessio/dsq

<!-- #public #snippet #sqlite -->

<!-- {BearID:810C0134-B05B-44C9-9037-C94CA2D7580D-1481-00000E25ACF07D01} -->
