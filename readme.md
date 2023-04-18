# Intro to Git

### Version control
* Track changes on files over time
* Retrieve a particular version when required
* Compare two versions
* Find out when a bug was introduced
* Provides change history
* Parallely work on different features with branch

### What's git?
**Git** is software for **tracking changes** in any set of files, usually used for coordinating work among programmers collaboratively developing source code during software development. Its goals include **speed**, **data integrity**, and support for **distributed**, **non-linear workflows** (thousands of parallel branches running on different systems).

### Why git?
* Open source
* Distributed
* Efficient with large projects
* Widely used/Popular

### Git setup
* Installation - [Git (git-scm.com)](http://git-scm.com/)
* User configuration
```
git config --global user.name "user name"
git config --global user.email "email@example.com"
git config --global --list
```

### Git help
* `git` will display a list of possible commands
* help specific to a command
	* `git <COMMAND_NAME> --help`
	* `git <COMMAND_NAME> -h`
	* `git help <COMMAND_NAME>`

## Basics commands
- `git init`
	- Initialise the git repository on the current folder
	- creates a `.git` folder that tracks the changes in the repository
	- `git remote add origin <URL>` to add a remote repo to a local repository
- `git clone <URL>`
	- Clones the source code from a report  repo to the current directoryg
- `git status`
	- Check the current status of the repo
- `git log`, `git log --oneline`
	- logs all the transactions on the repo
	- other flags
		- `--author`
		- `--grep`
		- `--commithash1..commithash2`
		- `--after=<DATE>`
		- `--before=<DATE>`
		- `--after=<DATE> --before=<DATE>`
		- `--sinc=<DATE>`
		- `--until=<DATE>`
	

## Git workflow
* clone a repository `git clone <URL>`
* `git pull` to get the latest changes from the remote repo
* make changes as required
* compare the changes `git diff`, `git diff <FILE_PATH>/<FILE_NAME>`
* stage the modified changes using `git add .`, `git add <FILE_PATH>/<FILE_NAME>`
* commit the changes to the local git repository `git commit -m <COMMIT_MESSAGE>`
* push the changes to the remote repository `git push`

![[Pasted image 20220620075931.png]]

## Modifying things on git
* `git restore <FILE_NAME>` to restore a locally modified file
* `git restore --staged <FILE_NAME>` to restore a staged file, this will unstage the file and inorder to remove completely use `git restore <FILE_NAME>`
* `git commit --amend -m <NEW_MESSAGE>`  amend the commit message on the latest commit
* `git revert <COMMIT_HASH>` to revert a commit
	* If you revert an older commit then we might run into conflicts which needs to be resolved individually
* `git clean -i/-n/-f` to delete untracked file from the working directory
* `git rm --cached <FILE_NAME>` - to untrack a file being tracked on the repository

## Branching
Ability to branch out from the main/master branch to develop and contribute without messing with the main branch.

- `git branch` list the branches on the working directory of the repository
- `git branch <BRANCH_NAME>` creates a new branch with the specified the branch
- `git checkout <BRANCH_NAME>` switch to the specified branch
- `git checkout -b <BRANCH_NAME>` creates a new branches and switches to it
- `git branch -m <OLD_BRANCH_NAME> <NEW_BRANCH_NAME>`  to rename branches
- `git branch -m <NEW_BRANCH_NAME>` renames the current branch
- `git branch -d <BRANCH_NAME>` delete branch which is merged
- `git branch -D <BRANCH_NAME>` delete un merged branch
- `git push origin --delete <BRANCH_NAME>` delete from remote

## Git stash
Safely store work in progress files in a stash when we need to context switch and work on something different

* `git stash`, `git staths save "description"`, `git stash push -m "Message"`
	* `--keep-only` dont stash staged files
	* `-u` stash the untracked files
	* `--patch` go through the changed files one by one
* `git stash list`
* `git stash apply`, `git stash apply stash@{1}`
* `git stash pop`, `git stash pop stash@{1}`
* `git stash drop stash@{1}`
* `git stash clear`

## What is Git ignore
* We do not want to track all the files in a repository, use `.gitignore` file to list the files we dont want to track.
* Typically files like temporary files, log files, company binary files etc.
* Can use regular expressions 
	* `*.log`
	* `bin/`
	* `!security.log` - will not ignore this file 


## Merge & rebase
Merge is the process of merging the current branch with another branch
* `git merge <BRANCH_NASME>`
 ![[Pasted image 20220620132719.png]]

### Rebase
Moves the current branch to the tip of the rebased branch by re wrtitng the project history by creating new commits for each commit in the original branch

* Cleaner commit graphs
* Rewrite commits
* Squash commits
* delete commits
![[Pasted image 20220620132739.png]]

## References
[Git - Book (git-scm.com)](https://git-scm.com/book/en/v2)
[Git Tutorials and Training | Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials)
