---
title: Git branch
date: 2021-04-29 8:30:00 HH:MM:SS +0100
categories: [Development, Git, GitLab, GitHub]
tags: [development, git, gitlab, github]
---

## Create branches

### Create a local branch

Simply create a new branch and push it:

```shell
git checkout -b myCustomBranch
```

### Create a remote branch

Simply create a new branch and push it directly to the remote repository:

```shell
git checkout -b myCustomBranch
git push -u origin HEAD
```

## List branches

### List local branches only

```shell
git branch
  master
* myCustomBranch
```

### List local and remote branches

With `-a` argument:

```shell
git branch -a
  master
* myCustomBranch
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
  remotes/origin/myCustomBranch
```

### List with verbosity

The `-v` argument gives the commit the branch is on:

```shell
git branch -v
  master            a0ca238 Simple fix
* myCustomBranch    a0ca238 Simple fix
```

### List with more verbosity

The `-vv` argument gives the commit the branch is on and the corresponding remote branch:

```shell
git branch -vv
  master            a0ca238 [origin/master] Simple fix
* myCustomBranch    a0ca238 [origin/myCustomBranch] Simple fix
```

### Combine verbosity and remote branches details

With the combination of the `-avv` arguments:

```shell
git branch -avv
  master                            a0ca238 [origin/master] Simple fix
* myCustomBranch                    a0ca238 [origin/myCustomBranch] Simple fix
  remotes/origin/HEAD               -> origin/master
  remotes/origin/master             a0ca238 Simple fix
  remotes/origin/myCustomBranch     a0ca238 Simple fix
```

## Delete branches

### Delete a local branch

```shell
git branch -d myCustomBranch
```

### Delete a remote branch

```shell
git push origin --delete myCustomBranch
```
