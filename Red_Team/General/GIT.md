### New Repo

```
mkdir <repoName> && cd <repoName>
git init
mkdir <project-folders>
touch .gitignore
git add .
git commit -m "Adds repot structure for <app>"
git remote add origin https://github.com/NAP3XD/<repotname>.git
git push origin master

```

### Branches
```
git branch -b <branch-name>  // add a new branch
git checkout <branch-name>   // switch branch

git merge <branch-to-merge>  // branch to merge to current
```

### Clone
```
git clone <url>
git clone -branch <branch-name> <url-of-repo>  // clone branch other than main
```