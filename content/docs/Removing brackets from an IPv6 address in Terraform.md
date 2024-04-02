
---
title: "Removing brackets from an IPv6 address in Terraform"
date: 2024-02-01 21:24:41
lastmod: 2024-02-01 21:26:21
categories: ['terraform', 'snippet']
draft: false
---


# Removing brackets from an IPv6 address in Terraform

```
replace(openstack_compute_instance_v2.INSTANCENAME.access_ip_v6, "/[\\[\\]]/", "")

# If using counts
"${replace(element(openstack_compute_instance_v2.INSTANCENAME.*.access_ip_v6, count.index), "/[\\[\\]]/", "")}"
```

<!-- #terraform #public #snippet -->

<!-- {BearID:3A3ECF6C-3C10-4D6A-9807-6D8B17796FC6} -->
