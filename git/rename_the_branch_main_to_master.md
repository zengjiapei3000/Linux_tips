# Rename the branch `main` to `master`

1. `git branch -m main master` to rename local branch `main` to `master`.
2. `git push -u origin master` to push local branch `master` to `origin` remote repository.
3. `git remote set-head origin master` to change HEAD from `origin/main` to `origin/master`.
4. `git fetch origin master` to fetch from `origin/master` to local.
5. `git branch -r --delete origin/main` to delete remote `origin/main`.