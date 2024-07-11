
---
title: "tcpdump snippets"
date: 2023-03-13T17:53:11Z
lastmod: 2023-07-11T16:56:17Z
categories: ['tcpdump', 'snippet']
draft: false
---


# tcpdump snippets

## Watch IPv6 RAs
```
tcpdump -vvvv -ttt icmp6 and 'ip6[40] = 134'
```

## All the v6 traffic
```
tcpdump -i <interface> -vv ip6
```

<!-- #public #tcpdump #snippet -->

<!-- {BearID:AAA8ADDB-1B4E-49FE-A879-7B7DA951C086-1623-0000159BCE9B98F7} -->
