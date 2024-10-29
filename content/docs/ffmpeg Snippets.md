
---
title: "ffmpeg Snippets"
date: 2024-08-08T05:10:22Z
lastmod: 2024-08-08T05:12:12Z
categories: ['ffmpeg']
draft: false
---


# ffmpeg Snippets

## Ogg Vorbis to AAC
```
ffmpeg -i myaudio.ogg -c:a aac -vn -b:a 160k myaudio.m4a
```

## Image Sequence to H.264
```
ffmpeg -framerate 10 -pattern_type glob -i '*.jpg' -c:v libx264 -crf 18 -pix_fmt yuv420p out.mp4
```

<!-- #ffmpeg #public -->

<!-- {BearID:6D4DFCCD-ECA2-4D91-A9F6-B5FB8CEF21C8} -->
