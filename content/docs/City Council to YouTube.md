
---
title: "City Council to YouTube"
date: 2024-04-17 13:16:02
lastmod: 2024-05-02 22:21:15
categories: ['yyccc', 'ffmpeg', 'snippet', 'calgary']
draft: false
---


# City Council to YouTube

Thanks to qntmpkts on GitHub for the initial confirmation this is possible to take a HLS stream (m3u8) and send it to YouTube:
https://gist.github.com/qntmpkts/403a027a4bfe99812ebf8952c41f8789

Also check out ffmpeg’s documenation page on this: https://trac.ffmpeg.org/wiki/EncodingForStreamingSites

```
ffmpeg -re -i protocol://domain.tld/stream.m3u8 -c:v copy -c:a aac -ar 44100 -ab 128k -ac 2 -strict -2 -flags +global_header -bsf:a aac_adtstoasc -bufsize 3000k -f mp4 "rtmp://a.rtmp.youtube.com/live2/<STREAMNAME/KEY>"
```

## Calgary City Council Stream
Current Link: https://lin12.isilive.ca/live/calgarycc/live/chunklist.m3u8
(The 12 in the URL can change as there are multiple servers)

This link can be found most easily by going to https://video.isilive.ca/play/calgarycc/live and then looking at the network tab in your browser to find the m3u8 URL it’s hitting.

### Codec Details
HLS
H264 (Main), yuv420p, 1080p
AAC 48hz

```
ffmpeg -re -i https://lin12.isilive.ca/live/calgarycc/live/chunklist.m3u8 -c:v copy -c:a aac -ar 44100 -ab 128k -ac 2 -strict -2 -flags +global_header -bufsize 3000k -f flv "rtmp://a.rtmp.youtube.com/live2/STREAM_KEY"
```

## Test to local file

```
ffmpeg -re -i https://lin12.isilive.ca/live/calgarycc/live/chunklist.m3u8 -c:v copy -c:a aac -ar 44100 -ab 128k -ac 2 -strict -2 -flags +global_header -bsf:a aac_adtstoasc -bufsize 3000k -f mp4 test30seconds.mp4
```

## Test local file to YouTube

```
ffmpeg -re -i test30seconds.mp4 -c:v copy -c:a copy -strict -2 -flags +global_header -bufsize 3000k -f flv "rtmp://a.rtmp.youtube.com/live2/STREAM_KEY"
```

## Downloading a previous day’s stream
Don’t use ffmpeg since we aren’t needing to copy/transcode. `youtube-dl` is great.
```
youtube-dl -f 0 --hls-prefer-native https://vod.isilive.ca/nospace/hls/calgary/Council-_-Primary_Public-_-Hearing-_-Meeting-_-of-_-Council_2024-05-02-11-21.mp4/index.m3u8
```

## Notes from trying this
* The audio starts to fall apart whenever the stream switches after a long break. This is fixed by ensuring you re-encode the audio to aac like the original snippet.

## Other options
Other folks recommend using [OBS](https://new.reddit.com/r/Calgary/comments/1ccxaka/comment/l18bj8q/) to take the input and send to YouTube and then have more control over the stream.

<!-- #public #yyccc #ffmpeg #snippet #calgary -->

<!-- {BearID:B8174ABC-4511-47EC-BDF3-3A4EE79F1A46} -->
