# Gittest
Testing for all git operations, for practicing and improving git skills.

## Basic Operations
```
git clone <repo_address>
git add <file/foldername> (inside the git repo)
git commit -m 'commit_msg'
git push
git branch <branch_name>
git checkout <branch_name> (switch to the branch)
```
## Basic Use cases
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
Basically telling you the untracked file changes the status from `untracked` to `new file` and waiting to be commited to the repo. Also if the file is already in the repo directory, then by using `git add` will also show this msg directly.

If you modified any files, you could do a quick check which files are modified also by using `git status` and you can get the following info:
```
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
And if you commit but haven't push it to the repo, you can use git status to find the following info:
```
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Untracked files:
        .README.md.swp

nothing added to commit but untracked files present
```
And if you made other changes after the commit, you still can push but after your push you will get the following info if you do a `git status`
```
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        .README.md.swp

no changes added to commit (use "git add" and/or "git commit -a")
```
If you want to create a new branch, you can use `git branch node01` and switch to the branch by using `git checkout node01`.


## Advance operations
```
 
