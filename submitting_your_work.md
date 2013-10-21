### Important Git Commands

#### Git Workflow

```bash
    git init /// creates new git repository
    git add . /// adds files to staging
    git add --all ///adds files to staging (incl deleted) 
    git commit -m "<message>" /// moves files to repo
    git status /// checks the status of files
    git log /// shows history of commits
```

#### Remote Repositories (Github)

```bash
    git remote add origin <server url> /// maps server url to "origin"
    git pull <branch name> /// pulls a specific branch to local repo
    git push /// pushes local repo to remote repo
    git clone <server url> /// pulls remote repo to computer
```
#### Branching

```bash
    git branch -a /// shows all branches
    git branch <branch_name> /// creates <branch_name>
    git checkout <branch_name> /// switches to <branch_name>
    git merge <branch_name> /// brings new branch back to current branch
```
