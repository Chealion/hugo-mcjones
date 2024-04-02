
---
title: "Addigy and Launchd"
date: 2024-02-12 16:24:22
lastmod: 2024-02-12 17:14:41
categories: ['addigy', 'snippet', 'launchd']
draft: false
---


# Addigy and Launchd
Addigy records Launchd items in “Third-Party Agents” and “Third-Party Daemons”

You can make a monitoring item on it for when these facts change.

Alternatively use the API to take a look see:

```
curl --location --request GET 'https://prod.addigy.com/api/devices?client_id=CLIENT_ID&client_secret=SECRET' | jq '.[] | {"TAG": ."Asset Tag", "Agents": ."Third-Party Agents", "Daemons": ."Third-Party Daemons"}' | grep -v addigy | grep -v Nudge | grep -v munki
```

<!-- #addigy #snippet #launchd #public -->

<!-- {BearID:62F85941-08DA-4B7C-B234-4D3D20AA125B} -->
