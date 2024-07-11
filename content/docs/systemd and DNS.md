
---
title: "systemd and DNS"
date: 2023-07-31T04:21:54Z
lastmod: 2023-07-31T05:14:17Z
categories: ['systemd', 'snippet']
draft: false
---


# systemd and DNS

For systemd < v239 (18.04 and earlier):
`systemd-resolve`

For >= v239 (20.04 and later):
```
resolvectl
```

## Set DNS
```
systemd-resolve --set-dns 1.1.1.1 --interface eno1
resolvectl dns eno1 1.1.1.1
```

## Remove DNS entry
```
resolvectl dns eno1 ''
```


<!-- #public #systemd #snippet -->

<!-- {BearID:A7D51C3B-C9B4-4F8D-8D8A-6811A1A2FDED} -->
