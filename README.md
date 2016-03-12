# Git

## Info

* a local Git repo is a directory initialized with Git version controlling system
* Git data lives in `.git` directory
* `git` command operates from the root of the repo directory
* Git version controlling flows through 3 concepts: working tree aka working directory, staging area aka index being the buffer (cache) zone for changes on their way to commits, and an array of commits with HEAD pointer
* staging area (index) contains changes that are ready to be committed by adding them from the working tree; reverse to staging is unstaging
* HEAD normally points to the most recent commit
* push: propagate changes from a local repo to a remote repo; pull: propagate in the reverse direction

## Commands

### Init

    [inside a directory to init it as a Git repo] git init
    [copy a remote repo] git clone user@host:/path/to/repo
    [copy a remote repo] git clone ssh://user@host.tld/repo.git
    [copy a remote repo recursively] git clone --recursive ssh://user@domain.tld/repo.git
    git clone https://github.com/user/reponame.git

### Misc

    git status

### Staging

    [add everything in the current directory to the staging area] git add .
    git add '<wildcard>'
    git add <filepath>
    [unstage a file] git reset <filepath>
    [remove and stage the removal of multiple files] git rm '<wildcard>'
    [remove and stage the removal of a directory] git rm -r <dirpath>
    [amend the latest (unpublished) commit] git commit --amend
    [unstage with rm] git rm --cached ...

### Committing

    git commit -m "Commit message"
    [stage & commit changes in tracked files only] git commit -a

### Remote Repos

    [register a remote repo] git remote add <remotename> <repoaddress>
    git remote add origin https://github.com/user/reponame.git
    [list all added remotes] git remote -v
    [info on 'origin' remote] git remote show origin
    [track a remote repo] git remote add --track <remotebranchname> <remotename> <repoaddress>

### Pushing & Pulling

    [push 'master' branch to 'origin' remote repo] git push -u origin master
    [next push] git push
    git pull
    git pull origin master
    git pull && git diff HEAD
    [remember changes before pulling without committing] git stash
    [re-apply stashed changes] git stash apply
    [remove and apply stashed changes] git stash pop
    [get all changes from a remote repo without merging] git fetch origin
    [revert all to a remote repo] git fetch origin && git reset --hard origin/master

### History

    git log
    [for a file] git blame <filepath>
    [for a file over time] git log -p <filepath>
    [by author] git log --author=<authorname>
    [with changes only] git log --name-status
    [more succinct] git log --pretty=oneline
    [shortened] git log --oneline
    [more detailed] git log --summary
    [decorated] git log --graph --oneline --decorate --all
    git log --help

### Comparing

    [list changes to tracked files] git diff
    [compare commits] git diff <commit1> <commit2>
    [compare HEAD with staged] git diff --staged
    [compare branches] git diff <branchname1> <branchname2>

### Reverting

    [revert a file to its HEAD contents] git checkout -- <filepath>
    [revert to a commit] git revert --no-commit <targetcommit>..HEAD && git commit
    [hard revert working tree to HEAD] git reset --hard HEAD
    [revert a commit] git revert <commit>
    [revert to a file in a commit] git checkout <commit> <filepath>

### Branching

    [branch info] git branch
    [create a branch at HEAD & switch] git checkout -b <branchname>
    [just create a branch at HEAD] git branch <branchname>
    [switch] git checkout <branchname>
    [delete a merged branch] git branch -d <branchname>
    [delete a branch] git branch -D <branchname>
    [push a branch] git push origin <branchname>
    [delete a remote branch] git push origin --delete <branchname>

### Merging

    [from the destination branch] git merge <srcbranchname>
    [mark a file as merged] git add <filepath>

### Tagging

    [list tags] git tag
    [tag the latest commit] git tag -a v<X.Y.Z> -m '<title>'
    [tag the latest commit] git tag v<X.Y.Z>
    git tag v<X.Y.Z> <commit>
    [publish tags] git push --tags
