
---
title: Chrome Kiosk Mode and Revolving Tabs
date: 2022-07-28 14:07:56
lastmod: 2022-07-28 14:10:25
categories: ['chrome']
draft: false
---


# Chrome Kiosk Mode and Revolving Tabs
TIL you can use Chrome to open multiple tabs in kiosk (no menu, no UI mode).

On macOS you can launch it with the `—kiosk` flag and then follow it with any number of `--app` arguments for the tabs. Combine this with an extension like [Revolver](https://chrome.google.com/webstore/detail/revolver-tabs/dlknooajieciikpedpldejhhijacnbda?hl=en) or [TabCarousel](https://chrome.google.com/webstore/detail/tabcarousel/ddldimidiliclngjipajmjjiakhbcohn?hl=en) and you’ve got a super simple and quick status page rotation setup.

If my particular case I’m running it on a separate old Mac mini:

```
ssh user@IP

screen

/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --kiosk --app "https://mcjones.ca" --app "https://chealion.ca"
```


<!-- #public #chrome -->

<!-- {BearID:73D7C24F-CCA4-4B8C-BE3D-AAA40EED31A8-22769-00000B031CECFA69} -->
