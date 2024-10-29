
---
title: "vim, ale, and fun"
date: 2024-04-12T03:43:54Z
lastmod: 2024-08-10T21:50:57Z
categories: ['vim', 'ale']
draft: false
---


# vim, ale, and fun
## ale
https://github.com/dense-analysis/ale  
Asynchronous Lint Engine

Ale is a fantastic syntax checker for vim and neovim and has made my life a lot easier.

## Toggling ale on and off
However there are many times I just want it to shut up so I can read the file in question…

```
:ALEToggle
:ALEDisable
:ALEEnable
```

## Customizing Ale
There are two use cases that Ale drives me nuts because while fantastic defaults I run into issues where they cause issues:

* Spell check
```
:set nospell
```


<!-- #public #vim #ale -->

<!-- {BearID:C1AF76CB-8BB5-44E7-A9EF-F8DD1580A388} -->
