
---
title: sips
date: 2022-06-21 17:31:27
lastmod: 2022-07-17 10:38:33
categories: ['macos']
draft: false
---


# sips
`sips` is awesome but I can never remember my most used cases.

## Square Image
Take a non-square image and “square it” - often for avatars and such.

```
sips -g pixelWidth test.png
sips -g pixelHieght test.png
# Set YYY to the max of the values above
sips -p YYY YYY test.png -o square.png
```

## Square to 16x10
```
sips Hubble_Deep_Field_SMACS0723.png -Z 1600x1600 -p 1600 3840 -o test.png
```

## Common flags
`-i` - add icon in Finder

<!-- #public #macos -->

<!-- {BearID:571EA800-1D33-4F17-9822-E9234F341200-1481-00000E988377EA6A} -->
