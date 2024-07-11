
---
title: "How to translate a name from _base back to it's original value?"
date: 2022-05-03T15:54:00Z
lastmod: 2024-06-23T19:19:20Z
categories: ['openstack', 'nova']
draft: false
---


# How to translate a name from _base back to it's original value?
Can we or is it a one way hash?

```
NAME=$(echo -n IMAGE_ID | openssl dgst -sha1)
```

SHA1 = one way hash

<!-- #public #openstack #nova -->

<!-- {BearID:981AA2D7-E68B-4D45-BE6E-E3059841C1BA-21964-000023CCDBF53421} -->
