---
title: Git and GitHub
author: Lukasz Laniewski-Wollk
output: html_document
---

# Git

Git is a program to track versions of source code (any text files really).
You can use it to preserve consecutive versions of your files on your disk to be able to go back to some old version.


## Basics

Generally first thing you do, is clone a repo:
```bash
git clone https://some.nice.adress/some/nice/repo.git
cd repo
```

After you modified some files, you do:
```bash
git add file.cpp
git commit -m "I added some nice file"
```

The first line says which files you want to include in your commit.
The second adds this commit to the storage and makes a note of "I added some nice file" for you to remember it by.

If you modify files that are already tracked by the repo, you can just do:
```bash
git commit -a -m "Frankly. I don't care anymore"
```

But ... you should not do it without first doing:

```bash
git status
```

Which will give you a summary of changes that are not yet commited, and which files are modified.
Generally: think good about what are you commiting.

## Branches

The most useful part of any versioning system (even more used then going back to old versions) is branching.
It's a simple concept of saying: "let me test this concept on the side, while the main version is still developed."
Many such side projects end up as dead ends.
Some of them end up being the only good version.
Sometimes they can be merged with the main version and live happly ever after.

So, to see what branches are in your current repo, do:
```bash
git branch
```

The current branch is conviniently marked.
If you want to create a new branch from the current state of the code, just do:
```bash
git checkout -b mybranch
```

Then add commits to it. If you want to switch back to the main branch (eg. `master`) do:
```bash
git checkout master
```

### Merge
Merge of a branch with another is just importing changes from another branch to yours.

!!! notice
    If you want to merge `mybranch` into `master`, first merge changes from `master` to `mybranch`

So, first thing you would do would be:

```bash
git checkout mybranch
git merge master
```

# Remote repos

The first things to remember is that **the repo on your disk is a copy of the repo on the server**.
That means that all changes have to be **pulled from** the server and **pushed to* the server.

!!! note "First fetch"
    The first thing you should do every time you sit to some development is `git fetch`

**Fetching** is the action of getting all the data from the server, but not updating your repo.
This means for instance that after it git can tell you that you're not up to date with the main repo.
Generally, even if at the moment you don't plan to **pull** or **push** it's a good idea to make git keep track of what is happening on the server.

The next thing is `git pull` which *will* update your repository.
This should be a simple update.
If at this stage something is in conflict or a merge occures, this means that you screwed up.
For example: you made some changes at work, pushed them to the server, then sat at home, made more differences, but didn't start by pulling the work changes from server.

# Forks and branches
The scheme of development in TCLB is that we generally **fork** the main repo on `github`, and then merge changes to the main repo by **pull requests**.

Let's say your name is Jim, and you forked the repo, first thing you do is:

```bash
git clone https://github.com/Jim/TCLB.git 
cd TCLB
git checkout develop
git pull
git remote add upstream  https://github.com/CFD-GO/TCLB.git
git fetch upstream
git pull upstream develop
```

