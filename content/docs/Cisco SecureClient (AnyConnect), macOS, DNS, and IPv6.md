
---
title: "Cisco SecureClient (AnyConnect), macOS, DNS, and IPv6"
date: 2025-04-29T09:39:32Z
lastmod: 2025-04-29T09:45:04Z
categories: ['macos']
draft: false
---


# Cisco SecureClient (AnyConnect), macOS, DNS, and IPv6
So you don’t have native IPv6 but now you have IPv6 via your VPN and DNS/connections just won’t work?

Welcome to a macOS feature that’s been around since 2018 to ignore IPv6 if your primary interface doesn’t support it.

While this was fixed for a bit in macOS 13.4 it came back.

Run BEFORE you connect to the VPN:
```
sudo scutil --disable-service-coupling on
```

Related Tunnelblick issue:
https://github.com/Tunnelblick/Tunnelblick/issues/490#issuecomment-447085756

<!-- #public #macos -->

<!-- {BearID:B1DBD96F-8449-448E-A597-BF470038EE65} -->
