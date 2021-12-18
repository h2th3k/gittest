# Gittest
Testing for all git operations, for practicing and improving git skills.

## Basic Operations
```
git clone <repo_address>
git add <file/foldername> (inside the git repo)
git commit -m 'commit_msg'
git push
```
## Use cases
Add a file to the repo
```
cp ~/testfile ./ ($pwd is the repo)
```
Then by using git status you will see the following msg:
```
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        testfile

nothing added to commit but untracked files present (use "git add" to track)
```
After you using `git add testfile` (which will add the file to the repo) you will see the following information:
```
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   testfile
```
Basically telling you the untracked file changes the status from `untracked` to `new file` and waiting to be commited to the repo. 
