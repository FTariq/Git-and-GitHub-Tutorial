# How to use Github!

## Creating a repository

There are two ways to start a repository. You can create and clone a Github repository, or create a local repository and then push to a Github repository.  

To clone, create an initial repo on Github, with a name, description, and a README.md (this will ensure a master branch has been created). Then to clone this repo to your current local directory:
```
git clone [URL]
```
If you wish to use existing local files and directories, you can create a local repository instead (include a README.md for good practice, as well as if there are no existing files in this directory):
```
echo "# test2" >> README.md / touch README.md
git init
```
## Making changes
Now that a repository has been created, navigate to it and make changes as you see fit. Then:
```
git add -A
git commit -m "first commit"
```
When you want to add changes to your Github repo, create an entry in your git config that specifies a name for the Github repo, to save using the URL every time. We will call this 'origin'.  
```
## Pushing to Github
git remote add origin [URL]
```
Now, we can push any commits to the Github repo by doing:
```
git push -u origin master
```
