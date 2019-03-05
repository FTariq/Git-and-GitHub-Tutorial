# How to start using Git and GitHub!
Just a reference for me as I'm finally starting to use GitHub, but I made it public as it could help anyone else starting out too! Compiled from many sources online and through experimenting with commands. Make sure you've read through the short introductory GitHub guide [here](https://guides.github.com/activities/hello-world/) installed Git from [here](https://git-scm.com/downloads) and configured your GitHub account to it before doing anything here: details can be seen on [this document](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf) (which also explains the most used commands). Additionally, if you want to avoid authenticating yourself every time you push and pull, generate an SSH key by following the steps [here](https://help.github.com/articles/connecting-to-github-with-ssh/).

The main process of git:
```
git init - creates a repository i.e. storing all the history of your project
git add - adds files to be 'staged' i.e. letting git know you want to save changes to this file
git commit - save all changes made to staged files
git push - send changes to your remote repository, for example on Github
git pull - get the latest version of the repository from your remote location
```

## Creating a repository

Git creates a 'repository' to store our complete file history, insertions/deletions made, backups of previous versions, and so on: this is the main gist of version control. There are two ways to start a repository. You can create and clone a GitHub repository, or create a local repository and then push to a GitHub repository.  

To clone, create an initial repo on GitHub, with a name, description, and a README.md (a testing file such as this is necessary for the rest of this tutorial, and it's good practice to do so anyway). Then to clone this repo to your current local directory:
```
git clone [URL]
```
If you then change the GitHub repository further, and you wish to update the local repository, you can simply run:
```
git pull
```
If you wish to use existing local files and directories instead, you can create a local repository for the current directory (include a README.md if there are no existing files in this directory, and also again for good practice):
```
echo "# test" >> README.md - this creates a README file containing a simple test comment
git init
```
Repositories can be created in other folders by doing ```git init [folder name]```. The command creates a .git folder and thus the git repository in the target directory. 
## Making changes
Now that a repository has been created, navigate to it and make changes to any files in this directory as you see fit. Then add all files to be staged (individually or all by using -A), and save changes to the branch by committing. 
```
git add -A
git commit -m "some comment about changes made"
```
A very useful command is:
```
git status
```
This outputs the current branch and files which have been or are yet to be staged and/or committed.  

If there are certain files/directories in this directory that you wish not to add, but you would still like to use ```-A```, you can create a ```.gitignore``` file and simply add each file and directory to omit on separate lines (this only works if they haven't already been added to the repository yet).

A branch is just a reference to a commit, and so a branch is not made when the repo is initialised, but only when a commit has been made: hence a README.md file is very useful for testing and committing!
## Branches and merging
The following commands view all existing branches, creates a new branch 'br', and then navigates to br:
```
git branch
git branch br
git checkout br
```
The latter two commands can be simplified via the command:
``` 
git checkout -b br 
```
Changes can then be made to the new branch br. To view the differences between commits, and then merge the master branch to br, do:
```
git checkout master - navigate to the master branch to merge with the new branch
git diff br - to compare differences between branches
git merge br - add the changes made to br to master
```
## Pushing and pulling
When you want to add changes to your GitHub repo, create an entry in your git config that specifies a name for the GitHub repo, to save using the URL every time. We will call this 'origin'. This is already done for you if you've cloned your repo (with its default name being 'origin' as well).
```
git remote add origin [URL]
```
The address of origin can be checked by replacing ```add``` with ```show```.

Now, we can push any commits to the GitHub repo by configuring the upstream/remote server using ```-u```. The upstream server is where we are pushing to (in this case 'origin'), and which branch we are using (in this case, 'master'). Subsequent push and pull commands can then be simplified as git now knows the default branch to upload and modify.
```
git push -u origin master
```
Now if there have been any changes to the GitHub files on the master branch and you wish to locally change them, or if you want to push again (both for the same remote server and branch), you can simply run:
```
git pull
git push
```
Note that for other branches, you would still have to write 'origin [branch name]' after any push or pull command, but without the '-u' (unless you want to change push/pull's default origin and branch). 

Note that ```git push``` is a combination of the two commands:
```
git fetch
git merge master origin/master
```
The former command 'fetches' the origin branch posted on GitHub (the remote repository), so that a local copy of the branch is made. We can then merge this branch, which has the default name of 'origin/master' with our local master branch. You could also change ```merge``` to ```diff```, to compare differences between the local and remote branches. 

A quick note, but for group projects, it is **highly** recommended to push and pull regularly - this will help to avoid the dreaded merge conflict! 

Creating a 'pull request' means that you wish to merge a branch you have forked (i.e. creating a copy of a repo to your own account) from another user's repository with your master branch. This may be as you have fixed certain bugs in their repo, improved features, and so on. They can then approve your pull request to merge your branch to their master, meaning your branch is now the default!

Hopefully this has helped you to understand and use Git and GitHub a bit more. If you feel like this can be improved in any way, you could use the knowledge gained from this and create a pull request using your suggested changes!

Now go out there and start coding!
