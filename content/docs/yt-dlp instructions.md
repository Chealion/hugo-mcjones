
---
title: "yt-dlp instructions"
date: 2018-03-01T21:02:01Z
lastmod: 2026-03-26T03:16:10Z
categories: ['snippet']
draft: false
---


# yt-dlp instructions
https://github.com/yt-dlp/yt-dlp
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

## Partial Clips
https://www.reddit.com/r/youtubedl/wiki/howdoidownloadpartsofavideo/
```
yt-dlp -f "(bestvideo[ext=mp4]+bestaudio[ext=m4a]/bestvideo+bestaudio)[protocol\!*=dash]" --external-downloader ffmpeg --external-downloader-args "ffmpeg_i:-ss 00:00:00.00 -t 00:00:8.00" "https://www.youtube.com/watch?v=SCo2RMpiZx8"
```

<!-- #public #snippet -->

<!-- {BearID:72BDB959-8F4F-4432-B005-AAC34B9A8453-1780-00053142E40FEC96} -->
