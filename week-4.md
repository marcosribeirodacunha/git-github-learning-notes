# Introduction to Git and GitHub - Week 4

[Back to home](README.md)

## Summary

- [Pull Requests](#pull-requests)
  - [Concepts](#concepts)
  - [Basic workflow](#basic-workflow-for-collaborating)
  - [Typical workflow](#typical-pull-request-workflow)
  - [Updating a Pull Request](#updating-a-pull-request)
- [Squashing changes](#squashing-changes)
- [Code Reviews](#code-reviews)
- [Issue tracker](#issue-tracker)

## Pull Requests

### Concepts

**Forking** is a way of creating a copy of the given repository so that it belongs to our user. When forking a repo, GitHub will know which repo it forked from.

**Pull Request** is a commit or series of commits that you send to the owner of the repository so that they incorporate it into their tree.

[Back to start](#introduction-to-git-and-github-week-4)

### Basic workflow for collaborating

1. Create a fork of the repository;
2. Work on the local fork.
3. Merge the changes back into the main repository by creating a Pull Request.

[Back to start](#introduction-to-git-and-github-week-4)

### Typical Pull Request workflow

1. Create a fork of the repository;
2. Clone the repo to have a local copy;
3. Create a new branch;
4. Make the changes to the repo;
5. Commit the changes;
6. Push the changes to the remote branch repo;
7. Create a Pull Request (click the _Pull request_ link);
8. Click _Create pull request_ button.

**P.S.:** if after step 7 GitHub notifies us that it's not able to merge the changes automatically, it'll be necessary to rebase the changes before creating a Pull Request.

After creating a pull request, it will appear a number next to the name of the pull request which is the identifier of the the pull request which is used in GitHub to track issues and pull requests. We can access this pull request by using that identifier number.

[Back to start](#introduction-to-git-and-github-week-4)

### Updating a Pull Request

1. Make the changes to the repo as usually;
2. Push them back to the remote repository (remember to push them to the same branch as the created pull request);
3. Git will automatically add the new commits to the Pull Request.

[Back to start](#introduction-to-git-and-github-week-4)

## Squashing Changes

`git rebase -i <branch_name>`: passing the `-i` flag (which means we're calling the _interactive_ rebase) will open the editor showing all the selected commits, so we can decide what we want to do by using keyword in before each commit hash.

Some keywords are:

`pick`: take the commits and rebase them against the branch we selected (_this is the **default** action_).
`reword`: reword a commit message keeping the changes as they are but modifying the commit messages.

`squash` and `fixup`: merge the commits into the **previous** commit in the list.

**When using** `squash` the commit messages are _added together_ and an editor opens up to let us make any necessary changes.
**When using** `fixup` the commit message for that commit is _discarded_

When rebasing for joining commits that is already in the remote branch, we'll get an error when try to push the new "rebased" commit. This happens because only the local branch will be rebased, so GitHub won't be able to Fast-forward the new commits in the repository. To force pushing once we know we're just squashing commits in one, we can run `git push -f` to force the push action.

[Back to start](#introduction-to-git-and-github-week-4)

## Code Reviews

Code reviews allow other people to look at the changes in the pull requests and suggest changes to that.

### Basic workflow (example)

Supposing it's requested to improve a README in the pull request, we can do the following:

1. Do any change requested in the local file;
2. Commit the changes and again join in only one commit. To avoid redoing the _squashing_ process explained above, it's possible to execute `git commit -a --amend` which means we're adding the files to the stage area (`-a` flag) and creating a new commit and then rebasing interactively with the keyword **_fixup_**. With this the commit gets replaced by a completely new commit with a completely different commit ID;
3. Push the changes using the `-f` flag;
4. On GitHub, looking at the Pull Request it's possible to notice the changes requested by code reviewers are marked with `outdated` flag, so we can now mark them as **resolved** by clicking on the button **_Resolve conversation_**.

[Back to start](#introduction-to-git-and-github-week-4)

## Issue tracker

GitHub has its own issue tracker where we can create a new issue explaining about the issue that we've noticed and possible solutions. As the Pull Requests, each issue has an exclusive hash tag.
When solving a issue it's possible to write in the commit message a "code" to close the specified issue by its hash tag. To do that we just need to write `Closes #<issue_id>` and this will automatically close the issue. e.g. `Closes #2` will close the issue #2.

[Back to start](#introduction-to-git-and-github-week-4)

[Back to home](README.md)
