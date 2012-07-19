# Git Commit and BugTrace

====

## Commit

```shell
git status
git add -A
git commit -a -m "commit detail"
git push
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


