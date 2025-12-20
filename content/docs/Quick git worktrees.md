
---
title: "Quick git worktrees"
date: 2025-12-19T23:11:16Z
lastmod: 2025-12-19T23:19:06Z
categories: ['git']
draft: false
---


# Quick git worktrees
You’re in your repo on some other branch and need a quick clone?
## Create
```
git worktree add ../<path> <branch>

git worktree add ../$(basename $(pwd))-main main
cd ../$(basename $(pwd))-main

git switch -c my-new-feature-branch
```

## Clean up
```
git worktree remove $(basename $(pwd))-main
```

<!-- #public #git -->

<!-- {BearID:B8750DB4-71EC-447D-803F-F0224136F53E} -->
