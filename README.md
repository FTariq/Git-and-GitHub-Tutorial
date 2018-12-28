# How to use Github!
Just a reference for me starting out to properly use Github, which could help anyone else out too!

## Creating a repository

There are two ways to start a repository. You can create and clone a Github repository, or create a local repository and then push to a Github repository.  

To clone, create an initial repo on Github, with a name, description, and a README.md (this will ensure a master branch has been created). Then to clone this repo to your current local directory:
```
git clone [URL]
```
If you wish to use existing local files and directories, you can create a local repository instead for the current directory (include a README.md for good practice, as well as if there are no existing files in this directory):
```
echo "# test" >> README.md
git init
```
Repositories can be created in other folders by adding the name of the repo to the end of the second command. Be aware that a branch is just a reference to a commit, and so a branch is not made in this second example until a commit has been made.
## Making changes
Now that a repository has been created, navigate to it and make changes as you see fit. Then add all files to be staged, and save changes by committing:
```
git add -A
git commit -m "initial comment"
```

## Pushing and Pulling
When you want to add changes to your Github repo, create an entry in your git config that specifies a name for the Github repo, to save using the URL every time. We will call this 'origin'. This is automatically done if you've cloned your repo.
```
git remote add origin [URL]
```
Now, we can push any commits to the Github repo by configuring the upstream/remote server: where we are pushing to, and pushing which specified branch. Subsequent push and pull commands can hence be simplified as git now knows the default branch to upload and modify (in this case, master).
```
git push -u origin master
```
