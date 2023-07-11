
---
title: "sips"
date: 2022-06-21 17:31:27
lastmod: 2023-04-09 23:54:01
categories: ['macos']
draft: false
---


# sips
`sips` is awesome but I can never remember my most used cases.

## Square Image
Take a non-square image and “square it” - often for avatars and such.

```
sips -g pixelWidth test.png
sips -g pixelHeight test.png
# Set YYY to the max of the values above
sips -p YYY YYY test.png -o square.png
```

## Whatever  to 16x10 
This is my go to command when downloading new images from the Webb Telescope.

```
sips Hubble_Deep_Field_SMACS0723.png -Z 1600x1600 -p 1600 3840 -o test.png
```

This doesn’t always work as expected (eg. Sips-300 with Ventura. If so, the `-Z` values need to be tweaked.

1. Find ratio of image (width/height)
	eg. 9474/4654 = 2.035
2. If greater than 2.4 (3840/1600) -  multiply 1600 by the ratio. To use for Z (1600*2.035 = 3256)
3. If ratio is less than 2.4 - multiply 3840 by the ratio. To use for Z (3840*2.035 = 7814)

```
sips MyImage.png -Z 7814x7814 -p 1600 3840 -o MyImage_CONVERT.png
```

## Crop to 16x10

```
sips SomeTallImage.png -Z 3840x3840 -p 1600 3840 --cropOffset 635 -800 -o test.png
```

The offsets (x,y) in pixels require quite a bit of tweaking based on the image being resized to the longest side being 3840.

### James Webb Telescope
https://webbtelescope.org/resource-gallery/images

The fact this page does not have an RSS feed maddens me.

## Common flags
`-i` - add icon in Finder

<!-- #public #macos -->

<!-- {BearID:571EA800-1D33-4F17-9822-E9234F341200-1481-00000E988377EA6A} -->
