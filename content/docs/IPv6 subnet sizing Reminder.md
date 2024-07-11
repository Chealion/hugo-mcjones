
---
title: "IPv6 subnet sizing Reminder"
date: 2024-06-16T18:42:36Z
lastmod: 2024-06-23T17:23:28Z
categories: ['ipv6']
draft: false
---


# IPv6 subnet sizing Reminder
* /64 - local subnet
* /56 (256 x /64) - site/subscriber
* /48 (65k /64 or 256 x /56) - if you know you want to give out /56s
* /32 - 65k x /48s

Generally you’ll use a /32 to give /48s.  
/48s will give /56s.  
/56s will give /64s  
And the smallest you go is the /64 (with some very minor exceptions)

<!-- #public #ipv6 -->

<!-- {BearID:71F64264-4608-4727-B4A0-8B9E127FAA93} -->
