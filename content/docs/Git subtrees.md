
---
title: Git subtrees
date: 587348480.808174
lastmod: 1657485693.86309
categories: ['git', 'snippet', 'git-subtree']
draft: false
---


# Git subtrees
## What’s the Problem?
How do you incorporate 3rd party code that you inevitably need to tweak to fit or want to track as part of your own repository?

eg. Public Puppet modules
Themes for Wordpress, Hugo, Ghost, etc.

## Git Options
Git offers two options - submodules and subtrees.

## Submodules
* Static
* Single Commit/Hash Reference
* Lots of overhead

Submodules reference a single hash/commit and as such require a lot of overhead. They are completely autonomous as distinct repositories. Which means if someone updates, it’s not updated for anyone else.

## Subtrees
* Import a repo as a directory
* Changes can go to upstream or part of your repository
* But with flexibility comes complexity

Subtrees meanwhile let you nest another repository as a directory. This allows you to make changes to that tree and keep those commits as part of your history while squashing the entire upstream history into a single commit. You can also update the module and keep your changes using standard git commands.

## Example
### Importing as a Subtree
```
mkdir my-fancy-repo
cd my-fancy-repo
git init .
touch README
git add .
git commit -m "My fancy repo begins"

git subtree add --prefix merge-parsers https://github.com/cybera/fortisiem-parsers master --squash

ls -laFh

git log --pretty
git remote -v
```

Kind of easy and we’ve merged a repo into ours, and it’s not tracking upstream.

### Tracking Subtrees
```
git remote add -f tracking-parsers https://github.com/cybera/fortisiem-parsers.git
git subtree add --prefix tracking-parsers https://github.com/cybera/fortisiem-parsers master --squash

ls -laFh

git log --pretty
git remote -v
```

Like the merge - we can now change the files in the module and commit the changes to our repository.

```
git remote add -f <name> <url>
git subtree add --prefix <path> <name> <branch/tag> --squash
```

### Updating Subtrees
```
git fetch tracking-parsers
git subtree pull --prefix tracking-parsers tracking-parsers master --squash
```

```
git subtree pull --prefix <path> <name> <branch/tag> --squash
```

### Pushing changes upstream
This will likely require some editing in a different branch - so that you are only pushing the changes you wish to send up.
```
git subtree push --prefix tracking-parsers tracking-parsers master
```

### Getting rid of subtrees
Chose the wrong subtree and want to get rid of it. It’s a bit more complicated.

#### Just removing
```
git rm path
git remote remove <origin>
git commit -m "Remove <x>"
```

And done. You do still have the history of that repo in your repo however.

#### Purging
If you want to recover the disk space, it’s a lot more involved and you’ll need to use `filter-branch` - see [StackOverflow](https://stackoverflow.com/questions/26107798/how-to-remove-previously-added-git-subtree-and-its-history) for the steps:
```
git filter-branch --index-filter 'git rm --cached --ignore-unmatch -rf <prefix>' --prune-empty -f HEAD
git reflog expire --expire-unreachable=now --all
git gc --prune=now
```

## Resources
 [https://www.atlassian.com/blog/git/alternatives-to-git-submodule-git-subtree](https://www.atlassian.com/blog/git/alternatives-to-git-submodule-git-subtree) 

. #public #git #snippet #git-subtree

<!-- {BearID:48B64C15-6289-47D9-9B96-54BE9DD6B1F4-794-000331C3B620C14A} -->
