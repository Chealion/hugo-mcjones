
---
title: "vim Snippets"
date: 2024-08-18T03:58:44Z
lastmod: 2024-08-18T04:10:44Z
categories: ['snippet', 'vim']
draft: false
---


# vim Snippets
## Moving around
* `f` and `F` will jump the character on the line that you enter. Shift F will go backwards.
* `t` and `T` are similar but will put you one character in front of where you want go
* `gu` and `gU` - and number for lines to make upper or lower case.

## Showing Spaces
```
:set listchars=eol:$,tab:>-,trail:~,space:␣
:set list
```

The `space:␣` is gold. Thank you [loxaxs](https://askubuntu.com/questions/74485/how-to-display-hidden-characters-in-vim#comment1621885_74503)!

## Preventing Indenting when Commenting
You’ll need to add the following to any filetype. (In this case we’re showing # and yaml)
```
set indentkeys-=0#

autocmd FileType yaml setlocal ts=2 sts=2 sw=2 expandtab indentkeys-=0#
```

## Block Editing

Enter visual mode: Control-V
Select lines: eg. 5j for the next 5 lines
Enter Insert with Shift-I
Type stuff/make changes
Hit Escape

<!-- #public #snippet #vim -->

<!-- {BearID:09311C43-4C73-4A67-B9F4-88E85BF628A3} -->
