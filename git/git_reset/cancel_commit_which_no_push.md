# 如何撤销已经写完但还没 push 的 commit

1. 获取日志: `git log`;
2. (二选一) 撤销并**保留**修改: `git reset {commit_id}`,
            撤销并**删除**修改: `git reset --hard {commit_id}`.
---
## 官方文档做法
### Undo a commit and redo
```
$ git commit ...
$ git reset --soft HEAD^      (1)
$ edit                        (2)
$ git commit -a -c ORIG_HEAD  (3)
```
1. This is most often done when you remembered what you just committed is incomplete, or you misspelled your commit message, or both. Leaves working tree as it was before "reset".

2. Make corrections to working tree files.

3. "reset" copies the old head to `.git/ORIG_HEAD`; redo the commit by starting with its log message. If you do not need to edit the message further, you can give `-C` option instead.

See also the --amend option to [git-commit(1)](file:///D:/Applications/Scoop/apps/git-with-openssh/2.34.1.windows.1/mingw64/share/doc/git-doc/git-commit.html).

### 个人尝试操作
```
git commit ...
git log                             # 此时已经能看到未提交的 commit
git reflog                          # 找到要reset的 reflog commit ID
git reset --soft {reflog_commit_ID}
git log
```
或:
```
git commit ...
git log                             # 此时已经能看到未提交的 commit
git reflog                          # 找到要reset的 reflog commit ID
git reset --soft HEAD
git log
```

完成撤销本地未 push 的 commit.