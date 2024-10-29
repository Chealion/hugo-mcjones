
---
title: "Using community.general.cloudflare_dns"
date: 2024-07-29T06:14:22Z
lastmod: 2024-07-29T06:14:54Z
categories: ['ansible', 'snippet']
draft: false
---


# Using community.general.cloudflare_dns
```
- name: Create AAAA record
  community.general.cloudflare_dns:
    zone: ZONE NAME
    record: "{{ ansible_hostname }}"
    type: AAAA
    value: "{{ ansible_default_ipv6.address }}"
    api_token: <TOKEN HERE>
```

<!-- #ansible #snippet #public -->

<!-- {BearID:D995CC11-3C4B-4D6B-968B-61D7306B9381} -->
