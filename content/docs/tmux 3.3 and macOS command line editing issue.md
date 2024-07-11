
---
title: "tmux 3.3 and macOS command line editing issue"
date: 2022-06-06T02:58:56Z
lastmod: 2022-10-04T04:20:13Z
categories: ['tmux', 'macos']
draft: false
---


# tmux 3.3 and macOS command line editing issue
```
micheal@~ % clear
terminals database is inaccessible
micheal@~ % echo $TERM
tmux-256color
```

https://github.com/tmux/tmux/issues/3203  
https://github.com/Homebrew/homebrew-core/issues/102748

The tl;dr is that the first release of tmux 3.3 on Homebrew had a bad default-terminal set for using it with macOS. This has been fixed by setting the following in .tmux.conf:

```
set-option -g default-terminal screen-256color
```

https://github.com/Chealion/dotfiles/commit/d0adef739b54df96b60c56b2774a2a0efa752bdd

<!-- #public #tmux #macos -->

<!-- {BearID:BEA39F40-ED41-4AF7-BEE7-2BF16DEF8BEE-49872-0000228C58EE9D3E} -->
