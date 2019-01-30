# How to start using Git and GitHub!
Just a reference for me as I'm finally starting to use GitHub, but I made it public as it could help anyone else starting out too! Compiled from many sources online and through experimenting with commands. Make sure you've installed Git from [here](https://git-scm.com/downloads) and configured your GitHub account to it before doing anything here: details can be seen on [this document](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf) (which also explains the most used commands). Additionally, if you want to avoid authenticating yourself every time you push and pull, generate an SSH key by following the steps [here](https://help.github.com/articles/connecting-to-github-with-ssh/).

## Creating a repository

We create a 'repository' with git to store our complete file history, insertions/deletions made, backups, and so on: this is the main gist of version control. There are two ways to start a repository. You can create and clone a GitHub repository, or create a local repository and then push to a GitHub repository.  

To clone, create an initial repo on GitHub, with a name, description, and a README.md (this will ensure a master branch has been created, and it's good practice to do so anyway). Then to clone this repo to your current local directory:
```
git clone [URL]
```
If you then change the GitHub repository further, and you wish to update the local repository, you can simply run:
```
git pull
```
If you wish to use existing local files and directories instead, you can create a local repository instead for the current directory (you could include a README.md for good practice, especially if there are no existing files in this directory):
```
echo "# test" >> README.md
git init
```
Repositories can be created in other folders by doing ```git init [folder name]```. The command creates a .git folder and thus the git repository in the target directory. 

Be aware that a branch is just a reference to a commit, and so a branch is not made when the repo is initialised, but only when a commit has been made: the README.md file could be used for testing and committing as seen below.
## Making changes
Now that a repository has been created, navigate to it and make changes to any files in this directory as you see fit. Then add all files to be staged (individually or all by using -A), and save changes to the branch by committing. 
```
git add -A
git commit -m "initial comment"
```
A very useful command is:
```
git status
```
This outputs the current branch and files which have been or are yet to be staged and/or committed.  

If there are certain files/directories in this directory that you wish not to add, but you would still like to use '-A', you can create a .gitignore file and simply add each file and directory to omit on separate lines (this only works if they haven't already been added to the repository yet).
## Branches and merging
The following commands view all existing branches, creates a new branch 'br', and then navigates to br:
```
git branch
git branch br
git checkout br
```
The latter two commands can be simplified by doing:
``` 
git checkout -b br 
```
Changes can be done by br, and to then view the differences between commits, and then merge, the master branch to br, do:
```
git checkout master
git diff br
git merge br
```
## Pushing and pulling
When you want to add changes to your GitHub repo, create an entry in your git config that specifies a name for the GitHub repo, to save using the URL every time. We will call this 'origin'. This is already done for you if you've cloned your repo.
```
git remote add origin [URL]
```
Now, we can push any commits to the GitHub repo by configuring the upstream/remote server (using -u): where we are pushing to, and pushing which specified branch. Subsequent push and pull commands can hence be simplified as git now knows the default branch to upload and modify (in this case, master).
```
git push -u origin master
```
Now if there have been any changes to the GitHub files on the master branch and you wish to locally change them, you can simply run:
```
git pull
```
Note that for other branches, you would still have to write 'origin [branch name]' after any push or pull command, but without the '-u'. Also note that this is a combination of the two commands:
```
git fetch
git merge master origin/master
```
The former command 'fetches' the origin branch posted on GitHub (the remote repository), so that a local copy of the branch is made. We can then merge this branch, which has the default name of 'origin/master' with our local master branch. You could also change ```merge``` to ```diff```, to compare differences between the local and remote branches.

Creating a 'pull request' means that you wish to merge a branch you have forked from another user's repository with your master branch. This may be as you have fixed certain bugs in their repo, improved features, and so on. They can then approve your pull request to merge your branch to their master, meaning your branch is now the default!

Now go out there and start coding!
