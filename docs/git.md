# Git Cheat Sheet

→ [git-scm.com](https://git-scm.com/)

## Learn

* [GitHub Guides > GitFlow](https://guides.github.com/introduction/flow/)
* [GitKraken > Learn Git](https://www.gitkraken.com/learn/git)

## Commands

```bash
# display Git client version
git version

# open the help for a given message (in the browser)
git help <command>

# see the current status of the local repository
git status

# know your reporistory origin URL
git config --get remote.origin.url
git remote -v

# update your origin URL
git remote set-url origin ssh://my.git.url

# reset to previous commit if already pushed
git reset --hard HEAD~1
git push origin HEAD --force

# reset to previous commit if not pushed
git reset HEAD~1

# list all local and remote branches
git branch -a

# fetch data from remotes
git fetch origin

# delete locally dev branch (on wrong remotes for instance)
git branch -d dev

# switch remotes (if branch has been deleted first)
git branch dev -t origin/dev
git checkout dev

# switch upstream on an existing branch
git branch --set-upstream-to=origin/dev dev

# push a branch (master) on a specific remote (other) by setting upstream to this remote
git push -u other master

# Navigate through the tags and branches
git log --graph --decorate --oneline --all

# Push on all remotes
git remote | xargs -L1 git push --all
```

## Recipes

* Rename your `master` branch to `main` (original idea from [hanselman.com](https://www.hanselman.com/blog/EasilyRenameYourGitDefaultBranchFromMasterToMain.aspx))

```bash
git branch -m master main
git push -u origin main
```

## Tools

* [GitKraken](https://www.gitkraken.com/): legendary Git GUI client for Windows, Mac & Linux
* [pre-commit](https://pre-commit.com/): a framework for managing and maintaining multi-language pre-commit hooks
