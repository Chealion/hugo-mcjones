
---
title: "Improving ImageOptim performance on Apple Silicon"
date: 2026-08-19T06:57:16Z
lastmod: 2026-08-19T06:59:26Z
categories: ['macos', 'imageoptim']
draft: false
---


# Improving ImageOptim performance on Apple Silicon
I always thought ImageOptim was a bit slower than I expected but never gave it much thought until I ran across the following PR: https://github.com/ImageOptim/ImageOptim/pull/466

As of August 2026 the current version is 1.9.3 which does not contain this merged fix from July 2026.

tl;dr - until that lands in a new release of ImageOptim.
```
defaults write net.pornel.ImageOptim RunLowPriority -bool false
```

<!-- #public #macos #imageoptim -->

<!-- {BearID:778DE74A-7FB0-4F42-A766-46175440CDF2} -->
