# restore-deleted-file-locally

sometimes, deleted working tree files can restore by git command `git checkout `.

## official reference method

The following sequence checks out the master branch, reverts the Makefile to two revisions back, deletes hello.c by mistake, and gets it back from the index.

```
$ git checkout master             (1)
$ git checkout master~2 Makefile  (2)
$ rm -f hello.c
$ git checkout hello.c            (3)
```

1. switch branch

2. take a file out of another commit

3. restore hello.c from the index

## my operation

when I deleted some files carelessly, type `git status` and input is that:

```
% git status                                                      [0] 
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    peter/.bashrc
        deleted:    peter/.config/yay/config.json
        deleted:    peter/.config/yay/config.json.bak
        deleted:    peter/.gitconfig
        deleted:    peter/.vim/.gvimrc
        deleted:    peter/.vim/.netrwhist
        deleted:    peter/.vim/.vimrc
        deleted:    peter/.vim/gvimrc_example.vim
        deleted:    peter/.vim/vimprc_example.vim
        deleted:    peter/.zshrc

no changes added to commit (use "git add" and/or "git commit -a")
```

I can use `git checkout <files>` to restore working tree files what I deleted.
```
% git checkout .                                                  [0] 
Updated 1 path from the index
```

and then check the files really restored!
```
% ls                                                              [0] 
etc  home  peter  README.md
```

Finished.