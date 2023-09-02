
---
title: "Git Snippets"
date: 2023-07-10 21:42:05
lastmod: 2023-08-28 15:47:13
categories: ['snippet', 'git']
draft: false
---


# Git Snippets
## Nuke all files not in the repo
```
git clean -df
```

`-n` is a dry run

## Add files already deleted
```
git add -u .
```

## Add files already deleted AND new files
```
git add -A
```

## Switching default upstream repo
```
git pull <upstream>
git pull --set-upstream origin main
```

## Updating a fork
```
git remote add upstream <upstream_url>
git fetch upstream
git merge <tag or branch name>
```

<!-- #public #snippet #git -->

<!-- {BearID:58309AF1-5B63-4195-BDB7-30C8DF50528F-4354-000000AE37996D86} -->
