# Tutorial
How to use Github!

There are two ways to start a repository. You can create and clone a Github repository, or create a local repository and then push to a Github repository.  

To clone:
Create initial repo on GitHub, with README.md
```
git clone [URL]
```
Or create a local repository:
```
echo "# test2" >> README.md / touch README.md
git init
```
Now that a repository has been created, navigate to it and make changes as you see fit. Then:
```
git add -A
git commit -m "first commit"
```
When you want to add changes to your Github repo, create an entry in your git config that specifies a name for the Github repo, to save using the URL every time. We will call this 'origin'.  
```
git remote add origin [URL]
```
Now, we can push any commits to the Github repo by doing:
```
git push -u origin master
```
