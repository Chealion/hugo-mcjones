
---
title: "Touch ID and sudo in macOS"
date: 2023-08-21 17:38:28
lastmod: 2023-09-26 12:14:22
categories: ['macos', 'snippet', 'sudo', 'touchid']
draft: false
---


# Touch ID and sudo in macOS

Had been meaning to do this for ages and now in Sonoma (macOS 14+) it can stick!

## Pre Sonoma
```
sudo sed -i '' '2a\
auth       sufficient     pam_tid.so\
' /etc/pam.d/sudo
```

## Post Sonoma
```
sudo cp /etc/pam.d/sudo_local.template /etc/pam.d/sudo_local
sudo sed -i '' 's/#auth/auth/g' /etc/pam.d/sudo_local
```

Latest source I used: https://sixcolors.com/post/2023/08/in-macos-sonoma-touch-id-for-sudo-can-survive-updates/

<!-- #public #macos #snippet #sudo #touchid -->

<!-- {BearID:BF194268-AFA0-4BDE-BF28-4C3B8D127865} -->
