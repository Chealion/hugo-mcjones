
---
title: "Pip / Virtual Environment Basics"
date: 2023-02-22T02:31:27Z
lastmod: 2025-04-20T17:59:58Z
categories: ['virtualenv', 'dev', 'python']
draft: false
---


# Pip / Virtual Environment Basics
## Setup
1. Install Command Line Tools for macOS and Homebrew
2. `brew install virtualenv`

## Why
Because Python packaging is a pain and different dependencies conflict. Using virtual environments separates your repos so you don’t need to worry about introducing a conflict unintentionally.

## Create and Use a virtual environment
```
cd ~/src/folder
<!-- #virtualenv venv -->
python3 -m venv venv
echo venv >> .gitignore
source venv/bin/activate
pip install -r requirements.txt
```

venv for the folder name is an arbitrary but consistent name used.
## Find out which requirements can be updated
```
pip list --outdated
```
## Update all dependencies
One liner to update all
```
pip3 list -o | cut -f1 -d' ' | tr " " "\n" | awk '{if(NR>=3)print}' | cut -d' ' -f1 | xargs -n1 pip3 install -U
```

After confirming the updates are fine

```
pip freeze > requirements.txt
```

And compare the changes.


<!-- #public #dev #python -->

<!-- {BearID:E58F9901-8C06-4FD6-9E59-A78BE798904D-3217-00000ED29FA9B297} -->
