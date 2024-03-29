# Git Cheat Sheet

→ [git-scm.com](https://git-scm.com/)

## Learn

* [GitHub Guides > GitFlow](https://guides.github.com/introduction/flow/)
* [GitKraken > Learn Git](https://www.gitkraken.com/learn/git)

## Commands

```bash
# displays Git client version
git version

# opens the help for a given message (in the browser)
git help <command>

# displays the current status of the local repository
git status

# displays the reporistory origin URL
git config --get remote.origin.url
git remote -v

# updates the origin URL
git remote set-url origin ssh://my.git.url

# resets to previous commit if already pushed
git reset --hard HEAD~1
git push origin HEAD --force

# resets to previous commit if not pushed
git reset HEAD~1

# lists all local and remote branches
git branch -a

# fetches data from remotes
git fetch origin

# deletes locally dev branch (on wrong remotes for instance)
git branch -d dev

# switches remotes (if branch has been deleted first)
git branch dev -t origin/dev
git checkout dev

# switches upstream on an existing branch
git branch --set-upstream-to=origin/dev dev

# pushes a branch (master) on a specific remote (other) by setting upstream to this remote
git push -u other master

# navigates through the tags and branches
git log --graph --decorate --oneline --all

# pushes on all remotes
git remote | xargs -L1 git push --all

# sets file as executable
git update-index --chmod=+x scripts/my_script.sh
```

## Recipes

* Rename your `master` branch to `main` (original idea from [hanselman.com](https://www.hanselman.com/blog/EasilyRenameYourGitDefaultBranchFromMasterToMain.aspx))

```bash
git branch -m master main
git push -u origin main
```

* SVN (Subversion) to git migration

  * [GitKraken - Migrating to Git from SVN](https://www.gitkraken.com/blog/migrating-git-svn)
  * [Azure DevOps - Learn how to migrate from Subversion (SVN) to Git, including history](https://docs.microsoft.com/en-us/azure/devops/repos/git/perform-migration-from-svn-to-git)

* Self-update git on Windows

```msdos
git update-git-for-windows
```

## Tools

* [GitKraken](https://www.gitkraken.com/): legendary Git GUI client for Windows, Mac & Linux
* [pre-commit](https://pre-commit.com/): a framework for managing and maintaining multi-language pre-commit hooks
