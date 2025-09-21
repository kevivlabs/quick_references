# GIT
## git basics
### git Porcelain ( high level)
- git status
- git add
- git pull
- git commit
- git push
- git log

### git plumbing (low level)
- git apply
- git commit-tree
- git hash-object
- git cat-file

### git config
- git config.get --user.name
- git config.get --user.email
- git config --global init.defaultBranch main (github specific)
- git config list
- git config --unset 
- git config list --local
- git config --unset-all example.key 
- git config --get 'key'
- Keys are in the format 'section'.'keyname' e.g user.name
- git config --remove-section section


## 40% of git 
- untracked /staged/ commited 
- to check " git status "
- to add use " git add 'filename' "
- to commit "git commit -m 'message' "

## git log
- git --no-pager log -n 10 
-  git log -n 10
commit 83edc0d7452116d7d65b6e541a23b96ab4b29729 (HEAD -> main)
- looking at .git/objects the folder will match first two characters 83 

## git cat-file 
- look at the contents of the commit hash git cat-file -p
 83edc0d7452116d7d65b6e541a23b96ab4b29729
- git cat-file -p 83edc0d7452116d7d65b6e541a23b96ab4b29729
tree 2eec2fbacfdb9e104e31fa37bc2be2476ee2e094
author kevivlabs <kevivlabs@domain.com> 1758438697 +0000
committer kevivlabs <kevivlabs@domain.com> 1758438697 +0000
- tree == folder 
- blob == file inside folder
- use git-file -p on tree hash then get the blob hash and run git-file on the blob hash to view contents

## locations
- system: /etc/gitconfig, a file that configures Git for all users on the system
global: ~/.gitconfig, a file that configures Git for all projects of a user
local: .git/config, a file that configures Git for a specific project
worktree: .git/config.worktree, a file that configures Git for part of a project 
- more specific overrides global
