
---
title: "yt-dlp instructions"
date: 2018-03-01 14:02:01
lastmod: 2023-10-30 21:58:11
categories: ['snippet']
draft: false
---


# yt-dlp instructions
```
# Formats
yt-dlp -F "https://www.youtube.com/watch?v=DIBw9dSVKdU"

# Easiest grab
yt-dlp -f bestvideo+bestaudio "https://www.youtube.com/watch?v=DIBw9dSVKdU"

or

# Stick with mp4/m4a
yt-dlp -f 'bestvideo[ext=mp4]+bestaudio[ext=m4a]/bestvideo+bestaudio' --merge-output-format mp4 "https://www.youtube.com/watch?v=DIBw9dSVKdU"

# Best m4a
yt-dlp -f 'bestaudio[ext=m4a]' -x "https://www.youtube.com/watch?v=II_5jBaYmGQ"

-x = extract audio
```

`yt-dlp` has been replaced with the `yt-dlp` fork

<!-- #public #snippet -->

<!-- {BearID:72BDB959-8F4F-4432-B005-AAC34B9A8453-1780-00053142E40FEC96} -->
