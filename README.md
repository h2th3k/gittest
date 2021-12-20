# Gittest
Testing for all git operations, for practicing and improving git skills.

## Basic Operations
```
git clone <repo_address>
git add <file/foldername> (inside the git repo)
git commit -m 'commit_msg'
git push
<<<<<<< HEAD
git branch <branch_name>
git checkout <branch_name> (switch to the branch)
```
## Basic Use Cases
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

After you using `git add testfile` (which will add the file to the repo) you will see the following information:

On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   testfile

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
<<<<<<< HEAD
```
If you want to create a new branch, you can use `git branch node01` and switch to the branch by using `git checkout node01`.


## Advance operations
```
git merge <branch_name/file_name>
```
## Advance Use Case

When you change a content in a sub-branch, and another guy changing the content on the same filethen when you trying to merge the sub-branch to the main branch by using `git merge sub_branch_name`(you are in main branch), there will be a problem,called conflict. The info will show like this:
```
Auto-merging 1
CONFLICT (content): Merge conflict in 1
Automatic merge failed; fix conflicts and then commit the result.
```

When you add create a file with name 1 and push to the main repo and another guy create a same file push to the subbranch repo, this will cause conflict as well and the info will show like this:
  
```
Auto-merging 2
CONFLICT (add/add): Merge conflict in 2
Automatic merge failed; fix conflicts and then commit the result. 
```
The solution of the conflict is that to mannully review the files or folder causing the conflict and change what is nessary. Normally, git will add mark in the files that causes conflict, and it looks like this:
```
`HEAD` indicates the changes are done by main, and node01 indicates the changes are done by subbranch. Remove or keep the changes base on your needs. After change you can use `git add` and `git commit` and `git push` to complete the merge.     
 ```
## Advance Use Case2
When both main branch and sub-branch changes the same file and pushed to the repo, this will cause conflict as mentioned above, when conflict happens you can use `git log` to see the log info, usually log info shows both of the sub-branch and main branch status. But under this case, the log will not show up the other one. A resolution will be using `git diff` to show which files different, and modify manually.

Difference will show like below:
```
Tuesday ---> same content between main and sub-branch
<<<<<<< HEAD
Wednesday ---> current content pointed by  head at sub-branch
=======
Monday ---> current content at main branch
>>>>>>> main
```
After resolving the difference, the confict will be gone. And if you do `git log` again, you can see the log info showing both main and sub-branch again.

Sometimes when you go `git merge main` you can will get
```
Already up to date.
```
That is because the `HEAD` pointing to the sub-branch which is (multiple) commits ahead of the main, and usually after a successful merge, you add something on the sub-branch which is not updated on the main branch yet, if you do `git log` you can see it more clearer.
```
commit 896af5bdb7924bb8ad195a2d12fc604cc1496ce2 (HEAD -> node01, origin/node01)                                                                                                                                     
commit 0b5046ce8a15cbf1125125ee8edc2de0e74a95c2 (origin/main, origin/HEAD, main)
```
In this case, if you want to keep main branch as the correct status, and in case you deleted files in the sub-branch and made current node of sub-branch ahead of main then be careful not use merge in main. Because this will apply the deletion on main as well. A resolution is to reset your branch node to the same node as main.
```
git reset --hard main //reset to main node
git push -f origin //force push to remote
```
If the local branch is already deleted, you can use `git push -f origin` to recover the files, this basically pushes the local branch master, but names it sub-branch on the remote. Then using `add .` to add the files back to local branch.

