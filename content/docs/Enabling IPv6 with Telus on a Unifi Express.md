
---
title: "Enabling IPv6 with Telus on a Unifi Express"
date: 2025-09-06T01:17:39Z
lastmod: 2025-09-06T01:20:44Z
categories: ['ubiquiti', 'telus']
draft: false
---


# Enabling IPv6 with Telus on a Unifi Express
## Internet Settings Page
| Setting | Value |
| --- | --- |
| IPv6 Connection | DHCPv6 |
| Prefix Delegation Size | 56 |

## Network Settings
Click the IPv6 tab!

| Setting | Value |
| --- | --- |
| Interface Type | Prefix Delegation |
| Prefix Delegation Interface | `<name of your WAN>` |

Once the prefix delegation goes through you’ll see your `/56` show up below Gateway IP/Subnet.

Using the auto settings (SLAAC) works great for my home network.

<!-- #public #ubiquiti #telus -->

<!-- {BearID:C9E8FF0B-489A-4C70-B58C-364A9FC826BA} -->
