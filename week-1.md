<h1 id="start">Introduction to Git and GitHub - Week 1</h1>

<p align="center">
  <a href="README.md">Back to home</a>&nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="week-2.md">Next week</a>
</p>

## Diff and Patch

The `diff` command show the difference between two files following this syntax:  
`diff first_file.js second_file.js`

When adding `> file_with_diff.js` at the end of the command, a file will be generated with only the differences.

The `patch` command applies the differences to the original file using this syntax:  
`patch original_file.js < file_with_diff.js`

## Git basics

The following commands are used to make simple settings to git:  
`git config --global user.name "name"`  
`git config --global user.email "email"`

To see all the settings for git, run the following command:  
`git config -l`

## Basic git workflow

`git add <file_name>`: add a file to the staging area. If file_name is replaced with `.` will add all files added or modified to the staging area.

`git status`: shows the actual state of the repository by showing the untracked, added, modified and deleted files and whether or not they are in the staging area.

`git commit`: create a new commit in the repository. If run without any flag it will open the predefined text editor to add a commit message. If used with the `-m` flag, it can write a message directly in the command, e.g. `git commit -m "Sample message"`.

`git log`: show all commits in the repository with some info such as the commit author, the date and the entire commit message.

<p align="center">
  <a href="README.md">Back to home</a>&nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="week-1.md">Next week</a>
</p>
