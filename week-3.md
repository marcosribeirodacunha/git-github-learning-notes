# Introduction to Git and GitHub - Week 3

[Back to home](README.md)

## GitHub basic interaction

`git clone <repo_url>`: clone/download a repository by using the given **repo_url**.

`git push`: send all the changes in the local repository to the remote repository.

`git pull`: retrieve new changes from the remote repository. This command is an alias for doing `git fetch` and after `git merge`.

`git config --global credentials.helper cache`: if we're using http to interact with remote repositories we'll be asked to pass our username and password every time (for actions like _git push_ or _git pull_). Therefore, using this command will allow git to cache our credentials once we pass them, then we won't need to pass them again on the next commands which require it, but only by 15 minutes.

`git remote`: List all the remote repositories.

`git remote -v`: show the urls for the remote repository, by showing the fetch and the push urls.

`git remote show <remote_name>`: show detailed information about the remote by given remote name (usually called **origin**).

`git branch -r`: show the remote branches that git are tracking.

`git fetch`: sync the data by copying the commits done in the remote repository to the remote branches.

`git log <remote_name/remote_branch>`: show the log for the given branch.

`git merge <remote_name/remote_branch>`: merge the changes of the given branch into the local branch.

`git remote update`: fetch the content of all remote branches and allow us to merge the contents ourselves.

## Solving conflicts

### Publishing remote branches

`git push <remote_name> <branch_name>`: publish to a remote branch. e.g. `git push origin master`.

### Rebasing

Rebasing means changing the base commit that's used for the branch. Rebasing the base where the commits split from the branch history, allows us to replay the new commits on top of the new base, allowing Git to do a fast forward merge, keeping the history linear.

`git rebase <branch_name>`: rebase a branch. This will move the current branch on top of the refactor branch.

### Basic rebasing flow (example 1)

- Go to the branch which we want to rebase (`git checkout refactor`);
- Run the rebase command (`git rebase refactor`);
- Return to the main branch (`git checkout master`);
- Merge the branch with the main branch (`git merge refactor`);
- Delete remote branch (`git push --delete origin refactor`);
- Delete local branch (`git branch -d refactor`);
- Push the changes to the remote repository (`git push`)

### Basic rebasing flow (example 2)

- Fetch the incoming changes (`git fetch`);
- Run the rebase the command (`git rebase origin/master`);
- Fix all the problems;
- Run command to continue the rebasing (`git rebase --continue`);
- Push the changes to the remote repository (`git push`);

### Best practices for collaboration

- Always sync the branches before starting any work;
- Avoid having very large changes that modify a lot of different things;
- When working on a big change, create a new separated feature branch;
- To make the final merge of the branch easier, regularly merge changes made on the master branch back onto the feature branch;
- If it's needed to maintain more than one version of a project at the same time, it's a good practice to have the latest version of the project in the master branch and a stable version of the project on a separated branch;
- When using these two branches, some bug fixes for the stable version may be done directly on the stable branch if they are no longer relevant to the latest version anymore;
- Avoid rebasing changes that have been pushed to remote repositories;
- Write good commit messages explaining the changes to provide the best context on why the changes were made;

[Back to home](README.md)
