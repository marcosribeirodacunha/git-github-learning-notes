# Introduction to Git and GitHub - Week 1

## Diff and Patch

The `diff` command show the difference between two files following this syntax:
`diff first_file.js second_file.js`

When adding `> file_with_diff.js` in the end of the command this file will be generated with only the differences.

The `patch` command applies the differences to the original file using this syntax:
`patch original_file.js < file_with_diff.js`

## Git basics

The following commands are used to make simple configurations to git:
`git config --global user.name "name"`
`git config --global user.email "email"`

To see all the configurations setup to git run the following command:
`git config -l` shows all git configuration

## Basic git workflow

`git add file_name`: add a file to the staging area. If file_name is replaced with . will add all files added or modified to the staging area.

`git status`: show actual state of the repository by showing the untracked, added, modified and deleted files and if they are or not in the staging area.

`git commit`: create a new commit in the repository. If run without any flag it will open the predefined editor text editor to add a commit message. If used with the `-m` flag, it can write a message directly in the command, e.g. `git commit -m "Sample message"`.

`git log`: show all commits in the repository with some info like, the author commit, the date and the whole message for the commit.
