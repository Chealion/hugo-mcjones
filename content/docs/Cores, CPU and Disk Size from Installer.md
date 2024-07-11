
---
title: "Cores, CPU and Disk Size from Installer"
date: 2017-04-05T17:17:07Z
lastmod: 2022-07-17T17:17:20Z
categories: ['snippet', 'macos']
draft: false
---


# Cores, CPU and Disk Size from Installer
Go to Terminal and run the following:

```
sysctl hw.physicalcpu
sysctl hw.memsize | awk '{ print $2/1024/1024/1024 " GB"}'
df -h
```

<!-- #snippet #public #macos -->

<!-- {BearID:9B191F56-7979-4F8C-AEE9-176CE63DBCBD-832-0002A4CD6777FFA0} -->
