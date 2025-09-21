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
- git log --oneline 
- git log --decorate=full

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

# git Branch 
- pointer to a specific commit
- git branch gives you where you are
- rename a branch 'git branch -m oldname newname'
- git branch 'mynewbranch' create new branch 
- 'git checkout mynewbranch ' old way of doing
- 'git switch -c my_new_branch'  create and switch to it
- 'git switch my_new_branch' just switch 
- information about branches are in .git/refs/heads/ 
- 'git branch -d branchname' to delete 
- git switch -c new_branch commithash (will create a new branch from that specific commit) 
- e.g git switch -c update_dune 98f0b6b (refering to D:)

# git merge 
## merge commit 
### e.g.
- 
```
   A - B - C - F    main
   \     /
    D - E        other_branch
```

```
*   89629a9 d234104 b8dfd64 (HEAD -> main) F: Merge branch 'add_classics'
|\
| * b8dfd64 fba0999 (tag: 5.8, add_classics) D: add classics
* | d234104 fba0999 (tag: 6.1) E: update contents
|/
* fba0999 1381199 (tag: 3.8, origin/master, origin/main, master) C: add quotes
* 1381199 a21228f (tag: 3.7) B: add titles.md
* a21228f A: add contents.md 
```
### e.g. explained 
- 89629a9 is the new merge commit hash. d234104 b8dfd64 is the parent commits

- F is the merge commit here, it has C and E are parents 
- you need to be in main and then run git merge other_branch
-  git log --oneline --graph --parents
- git commit --amend -m "F: Merge branch 'add_classics'"

## fast foward merge

- simplest form of merge
### e.g. 
- 
```
        C     other_branch
     /
A - B    main
```
```    
        other_branch
A - B - C   main

```
### e.g. explained  
- because branch delete_vscode has all commits that main has
- Git automatically does a fast-forward merge. It just moves the pointer of the "base" branch to the tip of the "feature" branch
- **no merge commit** is done on fast forward merge

## git rebase 
### e.g.
- 
```
A - B - C    main
   \
    D - E    feature_branch
``` 
- 
```
A - B - C         main
         \
          D - E   feature_branch
```

### e.g. explained
- we are working on feature branch but want to bring in changes from B and C into our branch
- we can merge main into our feature_branch but it causes new merge commit
- better way is to rebase, so replaying the commits from feature_branch on top of main. 
- basically include all changes in main branch 
- when on feature branch do git rebase main

## rebase vs merge 
- merge preserves the true history,shows when branches were merged and where. Can create a lot of merge commits,can make the history harder to read and understand.

- A linear history is  easier to read, understand, and work with. Some teams enforce the usage of one or the other on their main branch
- never rebase a public branch (like main) onto anything else.

# git reset
## soft 
- git reset 
    - undo the last commit(s) or any changes in the index (staged but not committed changes) and the worktree (unstaged and not committed changes).
- git reset --soft COMMIT HASH
    - --soft option is useful if you just want to go back to a previous commit, but keep all of your changes. Committed changes will be uncommitted and staged, while uncommitted changes will remain staged or unstaged as before.
- git reset --soft hash to go back to the I commit while keeping the changed titles.md (staged but not commited). J should be gone from the commit log.

## hard 

- git reset --hard COMMITHASH 
- hard not only undoes the commit but also the changes did
- soft will undo the commit and it will be stagging (added)
- **CAUTION** not recommended way of recovering files

# git remote

- by default in git, there is no source of truth
- github is considered central by convenience 
- remote can be anything
- the other repo is called remote , we call it origin but can be called anything
- git remote add 'name' 'uri' 
- e.g git remote add 'parent' '../parent'
- git fetch finds the .git/objects from remote and pulls in to local
- we need to git log remote/branch to get commits from remote branch
- git merge remote/branch this will merge remote to your local branch 

# git push 

- git push origin main push local main branch's commits to the remote origin's main branch
- git push origin localbranch:remotebranch push a local branch to a remote with a different name: 
- git push origin :remotebranch delete a remote branch by pushing an empty branch to it
