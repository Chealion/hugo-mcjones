
---
title: "SpamSieve and Exclude My Address Issue"
date: 2023-08-31 12:10:42
lastmod: 2023-08-31 12:15:21
categories: ['macos', 'spamsieve']
draft: false
---


# SpamSieve and Exclude My Address Issue
Source: https://forum.c-command.com/t/address-book-exclude-my-address-just-isnt-working/10879/7

1. Double check what addresses SpamSieve is getting from Contacts: Go to x-spamsieve://default?k=LogAddressBook&v=YES
2. Quit and reopen SpamSieve and open the Log
3. In my case it wasn’t seeing ANY of the emails from my contact card.

The fix?

https://c-command.com/spamsieve/help/exclude-my-addresses

```
defaults write com.c-command.SpamSieve ExtraAddressesToExclude -array a@b.com d@e.com
```

<!-- #public #macos #spamsieve -->

<!-- {BearID:3680B02D-FF49-4B50-B9FB-44167C1DEE4B} -->
