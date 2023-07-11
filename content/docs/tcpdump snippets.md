
---
title: "tcpdump snippets"
date: 2023-03-13 11:53:11
lastmod: 2023-03-13 11:54:00
categories: ['tcpdump', 'snippet']
draft: false
---


# tcpdump snippets

## Watch IPv6 RAs
```
tcpdump -vvvv -ttt icmp6 and 'ip6[40] = 134'
```

<!-- #public #tcpdump #snippet -->

<!-- {BearID:AAA8ADDB-1B4E-49FE-A879-7B7DA951C086-1623-0000159BCE9B98F7} -->
