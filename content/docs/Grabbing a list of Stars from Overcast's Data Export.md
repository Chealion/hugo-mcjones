
---
title: "Grabbing a list of Stars from Overcast's Data Export"
date: 2023-01-06 23:15:44
lastmod: 2023-09-04 19:50:20
categories: ['python', 'bear-app', 'overcast']
draft: false
---


# Grabbing a list of Stars from Overcast's Data Export
1. Go to https://overcast.fm/account
2. Download All your Data. This is a custom OPML file.

## Most Basic
```
grep userRecommendedDate overcast.opml
```

## XMLPath Fun
This requires xmllint to be installed. (Installed with Xcode or Homebrew)

Will output all of the feeds

```
xmllint -xpath '/opml/body/outline[@text="feeds"]/outline/outline[@userRecommendedDate]' overcast.opml
```

For myself I created a list of Overcast URLs:
```
xmllint -xpath '/opml/body/outline[@text="feeds"]/outline/outline[@userRecommendedDate]/@overcastUrl' --format overcast.opml | sed 's/ overcastUrl=\"//g' | sed 's/\"//g'
```

## Scripting
Sometimes you also just need to accept you can’t do a fun one liner and need to write a script.

As such I made one (available at https://gist.github.com/Chealion/e39a59ae487a7ce752a63d505c7872be)

Python 3, using XPaths above, turning it into a format, and then using [Bear’s callback URL](https://bear.app/xurlbuilder/create/) format to create new notes.

<!-- #public #python #bear-app #overcast -->

<!-- {BearID:82A7206F-42EB-4F10-9251-5F1603E7D2AF-28016-00002BBC39B34BFA} -->
