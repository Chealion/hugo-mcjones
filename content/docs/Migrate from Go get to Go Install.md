
---
title: "Migrate from Go get to Go Install"
date: 2022-06-06T02:37:47Z
lastmod: 2022-07-10T18:52:18Z
categories: ['golang']
draft: false
---


# Migrate from Go get to Go Install
https://go.dev/doc/go-get-install-deprecation

In Go 1.17, go get was deprecated.
In Go 1.18 it was disabled.

Use 
```
go install github.com/user/package@latest
```

The tl;dr is use install instead of get but updating is different.

Instead of `go get -u` you will use the same install command and modify the version tag (or keep with latest)

<!-- #public #golang -->

<!-- {BearID:D0A2DCBF-4895-4DBB-9298-077C88CB700E-49872-00002285414AAA31} -->
