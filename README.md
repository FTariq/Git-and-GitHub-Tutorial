# Tutorial
How to use Github!

Cloning a repository: 
Create initial repo on GitHub, with README.md
```
git clone [URL]
```
Or create a new repository on the command line:
```
echo "# test2" >> README.md / touch README.md
git init
```
```
git add -A
git commit -m "first commit"
git remote add origin https://github.com/FTariq/test2.git
git push -u origin master
```
