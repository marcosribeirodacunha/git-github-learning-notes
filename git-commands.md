# Useful Git commands

This file list some useful commands to interact with [Git](https://git-scm.com/).
If you want to look at a more contextualized information about this commands, look at the **_week-n_** files, where are notes with a context.

The commands are listed in a alphabetical order.

## Summary

- [Add](#git-add)
- [Branch](#git-branch)
- [Checkout](#git-checkout)
- [Commit](#git-commit)
- [Config](#git-config)
- [Diff](#git-checkout)
- [Log](#git-log)
- [Merge](#git-merge)
- [Push](#git-push)
- [Rebase](#git-rebase)
- [Remote](#git-remote)
- [Reset](#git-reset)
- [Revert](#git-revert)
- [Show](#git-show)
- [Status](#git-status)
- [More commands](#more-commands)

## `git add`

`git add <file_name>`: add a file to the staging area. If `file_name` is replaced with `.` will add all files added or modified to the staging area.

`git add -p`: shows the difference in the files and ask if we want to stage the changes.

[Back to start](#useful-git-commands)

## `git branch`

`git branch`: show all branches in the repository.

`git branch <name>`: create a new branch with the specified name.

`git branch -d <name>`: delete a branch for the given name.

`git branch -D <name>`: Forcibly deletes a branch for the given name.

`git branch -r`: show the remote branches that git are tracking.

[Back to start](#useful-git-commands)

## `git checkout`

`git checkout <file_name>`: change file back to the earlier commit state _(unstaged changes)_.

`git checkout <file_name> -p`: ask change by change if want to undo the change or not _(unstaged changes)_.

`git checkout <branch_name>`: change the current branch to the specified branch.

`git checkout -b <branch_name>`: create a new branch with the specified name and switch to this branch.

[Back to start](#useful-git-commands)

## `git commit`

`git commit`: create a new commit in the repository. If run without any flag it will open the predefined text editor to add a commit message.

`git commit -m`: create a commit with the message passed directly in the command, e.g. `git commit -m "Sample message"`.

`git commit -a`: commit without directly staging the files changes. This happen because it is a shortcut to stage any changes and commits them in one step. **But** this does **not** add any new files, so it only works with files that are already tracked.

`git commit --amend`: override the previous commit with the current staging area state. It can be called without any changing in staging area to edit commit message. **AVOID** amending commits that have already been made public (after pushing to the shared repository).

[Back to start](#useful-git-commands)

## `git config`

`git config --global user.name "name"`: set the global user name.

`git config --global user.email "email"`: set the global user email address.

_These configurations shown above will be user with the commit messages for showing the **author** of the commit._
_Using the flag `--global` make it reflect to all the local repositories created. To configure only for the actual repo, we can just omit the flag._

`git config --global credentials.helper cache`: cache our credentials, so once we pass them, we won't need to pass it again in the next commands which require it, but only by 15 minutes.

`git config -l` shows all git configuration

[Back to start](#useful-git-commands)

## `git diff`

`git diff <commit_id> <commit_id>`: show changes detailed in the files. It's the same as the `diff -u` command.

`git diff --staged`: show the difference in the files which are already staged. It is an alias to `--cached` flag.

[Back to start](#useful-git-commands)

## `git log`

`git log`: show all commits in the repository with some info like, the author commit, the date and the whole message for the commit.

`git log -number`: _number_ represents the number of commit want to be shown. e.g. `git log -4`.

`git log -p`: show the differences from the last commits. The **"p"** comes from the _patch_ witch represents the patch created.

`git log --stat` show which files were changed and how many lines were added or removed in the commit.

`git log --graph`: show a "graphical" visualization of the merging infos.

`git log --oneline`: show a simplified version of the log.

_The last two commnads can be user together to a better visualization experience. e.g `git log --graph --oneline`_

`git log <remote_name/remote_branch>`: show the log for the given branch.

[Back to start](#useful-git-commands)

## `git merge`

`git merge <branch_name>`: merge the specified branch in the current branch.

`git merge --abort`: If there are merge conflicts (meaning files are incompatible), _--abort_ can be used to abort the merge action.

[Back to start](#useful-git-commands)

## `git push`

`git push`: send all the changes in the local repository to the remote repository.

`git push <remote_name> <branch_name>`: publish to a remote branch. e.g. `git push origin master`.

`git push --delete <remote_name> <branch_name>`: delete a remote branch.

`git push -f`: to force the push action.

[Back to start](#useful-git-commands)

## `git rebase`

`git rebase <branch_name>`: rebase a branch. This will move the current branch on top of the refactor branch.

`git rebase --continue`: after solving the merge conflicts, run this to continue the rebasing.

`git rebase -i <branch_name>`: executes a interactive rebase where we can select what we want to do with each commit.

[Back to start](#useful-git-commands)

## `git remote`

`git remote`: List all the remote repositories.

`git remote -v`: show the urls for the remote repository, by showing the fetch and the push urls.

`git remote show <remote_name>`: show detailed information about the remote by given remote name (usually called **origin**).

`git remote update`: fetch the content of all remote branches and allow us to merge the contents ourselves.

[Back to start](#useful-git-commands)

## `git reset`

`git reset HEAD <file_name>`: reset file to untracked state _(staged changes)_.

`git reset HEAD <file_name> -p`: ask change by change if want to reset the changes or not _(staged changes)_.

[Back to start](#useful-git-commands)

## `git revert`

Create a commit that contains the inverse of all the changes made in the bad commit in order to cancel them out.

`git revert HEAD`: revert the last commit.

`git revert <commit_id>`: revert an specific commit by it **commit_id**. It's not necessary to pass the whole commit_id, but only the start of it (first 5 characters can be enough).

[Back to start](#useful-git-commands)

## `git show`

`git show <commit_id>`: allow us to see only the diff in the specific **commit id**.

`git show --name-only <commit_id>`: show only the commit info and the name of the files included in the commit.

[Back to start](#useful-git-commands)

## `git status`

`git status`: show actual state of the repository by showing the untracked, added, modified and deleted files and if they are or not in the staging area.

`git status -sb`: show the status in the short format (`-s` flag) and with the branch and tracking info (`-b` flag).

[Back to start](#useful-git-commands)

## More commands

`git clone <repo_url>`: clone/download a repository by using the given **repo_url**.

`git fetch`: sync the data by copying the commits done in the remote repository to the remote branches.

`git mv <old_name> <new_name>`: move/rename a file in the repository. Similar to Linux `mv` command.

`git pull`: retrieve new changes from the remote repository. This command is an alias for doing `git fetch` and after `git merge`.

`git rm <file_name>`: delete/remove a file from the repository. Similar to Linux `rm` command.

[Back to start](#useful-git-commands)
