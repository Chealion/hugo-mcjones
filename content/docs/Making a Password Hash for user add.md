
---
title: "Making a Password Hash for user add"
date: 2023-08-08T18:08:49Z
lastmod: 2023-08-08T18:16:59Z
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
