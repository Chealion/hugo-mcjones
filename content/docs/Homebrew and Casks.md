
---
title: "Homebrew and Casks"
date: 2021-12-25T02:33:03Z
lastmod: 2022-07-23T04:02:52Z
categories: ['List', 'homebrew', 'macos']
draft: false
---


# Homebrew and Casks
```
brew update
brew upgrade
brew outdated

<!-- #List outdated casks -->
brew outdated --cask --greedy

brew upgrade --cask <name> -f

for i in $(brew outdated --cask --greedy | awk '{ print $1 }'); do brew upgrade --cask ${i}; done
```

<!-- #public #homebrew #macos -->

<!-- {BearID:D78A5184-D038-438C-8299-C3F365537BA3-29797-000143A8642B5BAC} -->
