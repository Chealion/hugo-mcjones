
---
title: youtube-dlc instructions
date: 2018-03-01 14:02:01
lastmod: 2022-07-17 10:59:57
categories: ['snippet']
draft: false
---


# youtube-dlc instructions
```
# Formats
youtube-dlc -F "https://www.youtube.com/watch?v=DIBw9dSVKdU"

# Easiest grab
youtube-dlc -f bestvideo+bestaudio "https://www.youtube.com/watch?v=DIBw9dSVKdU"

or

# Stick with mp4/m4a
youtube-dlc -f 'bestvideo[ext=mp4]+bestaudio[ext=m4a]/bestvideo+bestaudio' --merge-output-format mp4 "https://www.youtube.com/watch?v=DIBw9dSVKdU"

# Best m4a
youtube-dlc -f 'bestaudio[ext=m4a]' -x "https://www.youtube.com/watch?v=II_5jBaYmGQ"

-x = extract audio
```

<!-- #public #snippet -->

<!-- {BearID:72BDB959-8F4F-4432-B005-AAC34B9A8453-1780-00053142E40FEC96} -->
