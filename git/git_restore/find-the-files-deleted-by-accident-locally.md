# find-the-files-deleted-by-accident-locally
When we delete some local files **by mistake**, we can sync pull to find deleted files.

## reference
https://git-scm.com/docs/git-checkout#Documentation/git-checkout.txt-emgitcheckoutem-p--patchlttree-ishgt--ltpathspecgt82308203

## operation
before operation(deleted some files)
```
D:\Github_Repositories\zengjiapei3000>git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)    
        deleted:    README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

1. use `git restore <file>...` to discard changes in working directory.
```
git restore *
```

2. `git pull <remote>` to get the remote files.
```
git pull origin
Enter passphrase for key '/c/Users/ash_258/.ssh/id_rsa': 
Already up to date.
```

Finish.