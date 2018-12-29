# How to start using Git and Github!
Just a reference for me as I'm finally starting to use Github, but I made it public as it could help anyone else starting out too! Compiled from many sources online and through experimenting with commands. Make sure you've installed Git and configured your Github account to it before doing anything here: details can be seen on [this document](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf) (which also explains the most used commands).

## Creating a repository

There are two ways to start a repository. You can create and clone a Github repository, or create a local repository and then push to a Github repository.  

To clone, create an initial repo on Github, with a name, description, and a README.md (this will ensure a master branch has been created). Then to clone this repo to your current local directory:
```
git clone [URL]
```
If you wish to use existing local files and directories, you can create a local repository instead for the current directory (you could include a README.md for good practice, especially if there are no existing files in this directory):
```
echo "# test" >> README.md
git init
```
Repositories can be created in other folders by adding the name of your repo to the end of the second command. Be aware that a branch is just a reference to a commit, and so a branch is not made when the repo is initialised, but only when a commit has been made: the README.md file could be used for testing and committing as seen below.
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
Changes can be done by br, and to then view the differences between, and then merge, the master branch to br, do:
```
git checkout master
git diff br
git merge br
```
## Pushing and pulling
When you want to add changes to your Github repo, create an entry in your git config that specifies a name for the Github repo, to save using the URL every time. We will call this 'origin'. This is already done for you if you've cloned your repo.
```
git remote add origin [URL]
```
Now, we can push any commits to the Github repo by configuring the upstream/remote server (using -u): where we are pushing to, and pushing which specified branch. Subsequent push and pull commands can hence be simplified as git now knows the default branch to upload and modify (in this case, master).
```
git push -u origin master
```
Now if there have been any changes to the Github files on the master branch and you wish to locally change them, you can simply run:
```
git pull
```
Note that for other branches, you would still have to write 'origin [branch name]' after any push or pull command, but without the '-u'.
