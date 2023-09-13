
---
title: "Making a Password Hash for user add"
date: 2023-08-08 12:08:49
lastmod: 2023-08-08 12:16:59
categories: ['snippet']
draft: false
---


# Making a Password Hash for user add

```
HASH=$(mkpasswd -m sha-512)

useradd -mp "${HASH}" -G sudo username
```

<!-- #public #snippet -->

<!-- {BearID:84589C27-CF54-40B6-AAC4-9C4FA1AF97BF} -->
