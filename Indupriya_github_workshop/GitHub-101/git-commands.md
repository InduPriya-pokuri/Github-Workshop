
## Git-Commands
Collection of git commands that you need to use quite often.

## Some great links:
* Git-Branching-Basic-Branching-and-Merging: https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging
* Git-Branching-Rebasing: https://git-scm.com/book/en/v2/Git-Branching-Rebasing
* Git-Tools-Stashing-and-Cleaning: https://git-scm.com/book/en/v2/Git-Tools-Stashing-and-Cleaning

## 🧑🏻User Config related commands:
* View user details:

  📝 `git config user.name`
 
  📝 `git config user.email`
* View all details:

  📝 `git config --list`
* Set details globally:

  📝 `git config --global user.name "<user_name>"`

  📝 `git config --global user.email "<email>"`

  Not recommended to use global settings, better use project level settings. Helpful if you have multiple accounts.
* Set details at project level:

  📝 `git config user.name "<user_name>"`

  📝 `git config user.email "<email>"`

## 🔁 Remote related commands:
* Get remote repository to local:

  📝 `git clone <repository_url>`

* List all existing remotes:

  📝 `git remote -v`

* Add remote:

  📝 `git remote add <remote_name> <repository_url>`

* Update/Change remote url:

  📝 `git remote set-url <existing_remote_name> <new_url>`

* Remove remote:

  📝 `git remote remove <remote_name>`

  More Explanation: http://help.github.com/articles/changing-a-remote-s-url

## 🤷🏻‍♂️ Ignore related commads:
* Ignore tracked files:

  📝 `git update-index --assume-unchanged <file>`


## 🌿 Branch related commands:
* View branches:

  📝 `git branch`

* Switch to a branch:

  📝 `git checkout <branch_name>`

* Switch to a branch igorning non-commited changes on current branch

  📝 `git checkout -f <branch_name>`

* Get a remote branch on local and switch to it:

  📝 `git fetch && git checkout <branch_name>`

* Cut a new branch from an existing branch and switch to the newly created branch:

  📝 `git checkout -b <new_branch_name> <existing_branch_name>`

* Save changes in the branch (on local):

  📝 `git commit` for bigger commit messages

  📝 `git commit -m "<commit_message>"` for smaller commit messages

* Push changes from local branch to remote branch:

  📝 `git push -u <remote_name> <branch_name>` if branch is created locally and it doesn't exist at remote yet,

  📝 `git push <remote_name> <branch_name>` otherwise
  
* Rename branch:

  📝 `git branch -m <new_name>` if on the branch that needs to be renamed: 

  📝 `git branch -m <old_name> <new_name>` if on different branch: 

  The above is enough if the branch only exists in your local, but if the branch has been pushed to remote, follow these two additional steps:

  📝 `git push origin :<old_name> <new_name>` This will delete old_name remote branch and push new_name local branch
  
  📝 `<switch to branch and> git push origin -u <new_name>`This will reset the upstream branch for the new-name local branch:

* Merge a branch with another:

  📝 `git checkout <destination_branch>`

  📝 `git merge <source_branch>`

  I typically merge using GUI(IntelliJ for Java Projects)
* Delete local branch:

  📝 `git branch -d <branch_name>`

  📝 `git branch -D <branch_name>` if you have uncommited/unmerged changes:
  
## 🔀 Revert related commands:
* Revert to older commits:

  📝 `git reset --hard <destination_commit_id>`

  If the commits that are being reverted were already pushed to remote do `git push --force` also, however, be very very careful, this will rewrite your history. You will lose the commit and is generally not a very nice thing to do in a collaborative environment.


* Pull changes from remote ignoring any local changes:

  📝 `git reset ---hard` to go to last commit and then,

  📝 `git pull <remote_name> <repository_url>`
  
* Unstage a file:

  📝 `git reset file/to/unstage`
  

* Edit a commit message which is not yet pushed

  📝 `git commit --amend` for bigger messages

  📝 `git commit --amend -m <new_commit_message>`

  If commits were already pushed to remote, update the remote too with below command

  📝 `git push <remote_name> <branch_name> -f` or `git push <remote_name> <branch_name> --force`


* Revert specific files to specific commit:

  📝 `git checkout <commit_id> -- <file1/to/restore> <file2/to/restore>`


* Recover a branch after its deleted:

  📝 `git checkout -b <branch_name> <sha>`

  To find sha do `git reflog` or in case you have just deleted your branch, then scroll up in terminal to find something like `Deleted branch <your_branch> (was <sha>)`
