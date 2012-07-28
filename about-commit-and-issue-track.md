# Git Commit and BugTrace

====

## Install

http://git-scm.com/

or

http://github.com

## Commit

```shell
git status
git add -A
git commit -a -m "commit detail"
git push
```

## Pull-Request

http://www.worldhello.net/gotgithub/04-work-with-others/010-fork-and-pull.html

```shell
git add remote cooper git@github.com:codesharp/cooper.git
git remote -v
git fetch cooper
git branch -a
git merge cooper/master
git log --graph -2
```

## Pull-Request With Local Repos

http://stackoverflow.com/questions/5775580/git-pulling-changes-between-two-local-repositories

that's cool!

```shell
git add remote cooper-local ../../codesharp/cooper
git remote -v
git fetch cooper-local
git branch -a
git merge cooper-local/master
```

## BugTrace

use [github issues](https://github.com/codesharp/infrastructure/issues) to bugtrace.

before fix bugs, always create issues to record them.


## Link Commit to Issue

1. create issue #1.

2. link both of them with commit:

```shell
git commit -a -m "fix #1, other messages"
```



