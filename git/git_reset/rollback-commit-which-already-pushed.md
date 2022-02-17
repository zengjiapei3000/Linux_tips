# rollback-commit-which-already-pushed

sometimes, we want to rollback to commit when already pushed.

## official reference method

Undo commits permanently

```
$ git commit ...
$ git reset --hard HEAD~3   (1)
```

1. The last three commits (HEAD, HEAD^, and HEAD~2) were bad and you do not want to ever see them again. Do not do this if you have already given these commits to somebody else. (See the "RECOVERING FROM UPSTREAM REBASE" section in git-rebase[[1](https://git-scm.com/docs/git-rebase)] for the implications of doing so.)

## my operation

After I push some bad commit to remote, I rollback the previous one commit:
```
% git reset --hard HEAD@{1}
% git push origin master --force
```