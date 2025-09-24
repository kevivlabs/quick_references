# git advanced

## git config
- git config --local rerere.enabled false 
- rm -rf .git/rr-cache

## git PR
- git push remote local-branch:remote-branch
- git push origin add_contrib:add_contrib

## git head
- HEAD references to commits and refers to branch you are currently in

## git reflog
- like git log but shows history of a branch or Head 
-
```
labs@ubuntu24:~/dev/gitlearning/megacorp$ git reflog
0d16f95 (HEAD -> main, origin/main, origin/HEAD) HEAD@{0}: checkout: moving from slander to main
315e820 HEAD@{1}: commit: B: slander
git reflog (find the commit sha at HEAD@{1})
git cat-file -p <commit sha>
git cat-file -p <tree sha>
git cat-file -p <blob sha> > slander.md
git add .
git commit -m "B: recovery"
```
- use git cat-file -p on the commit to go and recover here 315e820
- then tree , then blob 

## git merge 'commitish'

- better way to recover files
- git merge HEAD@{1}

## git conflict
- <<<<<<< HEAD and ======= lines, is our branch's version of the file. The bottom section, between the ======= and >>>>>>> main lines, is the version of the file that's on the main branch

## git checkout 
- checkout individual changes 
- git checkout --ours/theirs
- 
    --ours will overwrite the file with the changes from the branch you are currently on and merging into
    --theirs will overwrite the file with the changes from the branch you are merging into the current branch
- git checkout --theirs path/to/file ( keep their change)
- git checkout --ours path/to/file (keep our change)
