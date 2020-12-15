<h1 id="start">Introduction to Git and GitHub - Week 2</h1>

<p align="center">
  <a href="week-1.md">Previous week</a>&nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="README.md">Back to home</a>&nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="week-3.md">Next week</a>
</p>

## Summary

- [Git interaction](#git-interaction)
- [Gitignore files](#gitignore-files)
- [Undoing changes](#undoing-changes)
- [Rollbacks](#rollbacks)
- [Branching and Merging](#branching-and-merging)

## Git interaction

### HEAD alias

In Git, HEAD represents the currently checked-out snapshot of the project.

### `git commit`

`git commit -a`: commit without directly staging the files changes. This happen because it is a shortcut to stage any changes and commit them in one step. **But** this does not add any new files, so it only works with files that are already tracked.

### `git log`

`git log -p`: show the differences from the last commits. The **"p"** comes from the _patch_ witch represents the patch created.

`git log --stat` show which files were changed and how many lines were added or removed in the commit.

`git log -n`: _n_ represents the number of commits we want to display.

### `git show`

`git show <commit_id>` allow us to see only the diff in the specific **commit id**.

### `git diff`

`git diff <commit_id> <commit_id>`: show changes in detail in the files. It's the same as the `diff -u` command.

`git diff --staged`: show the difference in the files which are already staged. It is an alias to `--cached` flag.

### `git add`

`git add -p`: shows the difference in the files and ask if we want to stage the changes.

### More commands

`git rm <file_name>`: delete/remove a file from the repository. Similar to Linux `rm` command.

`git mv <old_name> <new_name>`: move/rename a file in the repository. Similar to Linux `mv` command.

[Back to start](#start)

## `.gitignore` files

.gitignore files are used to tell the git tool to intentionally ignore some files in a given Git repository. For example, this can be useful for configuration files or metadata files that a user may not want to check into the master branch.

[Back to start](#start)

## Undoing changes

### `git checkout`

Use to undo changes **before** staging (unstaged changes).

`git checkout <file_name>`: change file back to the earlier commit state.

`git checkout <file_name> -p`: ask change by change if want to undo the change or not.

### `git reset`

Use to undo changes **after** staging (staged changes).

`git reset HEAD <file_name>`: reset file to untracked state.

`git reset HEAD <file_name> -p`: ask change by change if want to reset the changes or not.

### `git commit`

`git commit --amend`: override the previous commit with the current state of the staging area. It can be called without any changing in staging area to edit commit message. **AVOID** amending commits that have already been made public (after pushing to the shared repository).

[Back to start](#start)

## Rollbacks

### `git revert`

Create a commit that contains the inverse of all the changes made in the bad commit in order to cancel them out. Using it, it's possible to undo the changes, but leave the history of the commits in the project consistent, leaving a record of exactly what happened.

`git revert HEAD`: revert the last commit.

`git revert <commit_id>`: reverses an specific commit by its **commit_id**. It's not necessary to pass the entire commit_id, but only the beginning (first 5 characters can be enough).

[Back to start](#start)

## Branching and Merging

### Branches

A Branch is a pointer to a particular commit. It represents and independent line of development in a project.
The _default_ branch is the **master**.

`git branch`: show all branches in the repository.

`git branch <name>`: create a new branch with the specified name.

`git branch -d <name>`: delete a branch for the given name.

`git branch -D <name>`: Forcibly deletes a branch for the given name.

`git checkout <branch_name>`: change the current branch to the specified branch.

`git checkout -b <branch_name>`: create a new branch with the specified name and switch to this branch.

### Merge and Merge conflicts

Merging is the term that Git uses for combining branched data and history together.

`git merge <branch_name>`: merge the specified branch in the current branch.

`git merge --abort`: If there are merge conflicts (meaning files are incompatible), --abort can be used to abort the merge action.

There are two algorithms git uses for merging. One is fast-forward witch is used when there's no changes in the same file, and the other one is three-way merge, that is used when there's changes in the same file in the merged branches.

When a conflict occurs git will alert us to solve the conflict. So, we can see which files have conflicts by using `git status` and then deep into each one of those to solve the conflicts. In the end, we can simply add each one of these files by using `git add` and commit the changes.

After committing the merge, we can use the `git log --graph --oneline` to see a graphical and simplified information about the merging.

[Back to start](#start)

<p align="center">
  <a href="week-1.md">Previous week</a>&nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="README.md">Back to home</a>&nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="week-3.md">Next week</a>
</p>
