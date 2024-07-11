
---
title: "Go Module Handling"
date: 2023-02-17T07:01:58Z
lastmod: 2023-02-22T02:34:39Z
categories: ['dev', 'golang']
draft: false
---


# Go Module Handling
## Starting from Scratch
```
go mod init <name of your app>
go mod download <dependency>
go mod tidy
```

## Updating
https://go.dev/doc/modules/managing-dependencies#discovering_updates
```
go list -m -u all

go get -d -u -t ./...

go mod tidy
```

## Removing
```
go get example.com/theirmodule@none
```

Or remove from your files and run
```
go mod tidy
```


<!-- #public #dev #golang -->

<!-- {BearID:D582B1C7-5101-47F0-BED6-3C126CED84FB-3217-000005BF3A4ED609} -->
