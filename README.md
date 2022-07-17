# Hello World
Hello World repository for Git tutorial
This is an example repository for the Git tutorial on W3school.com

This repository is is built step by step in the tutorial.

This repository now includes steps for GitHub

# Git commands and their use
 //global -> set the username and email for every repository on your computer  
 //remove global to set username and email for current repo only.   
 git config --global user.name "<author/userName>"   
 git config --global user.email "<email-registered-with-GitHub>"  

 <br><br>
 //cd into the project repository
 
 git init

 
 //check all file including hidden
 
 ls -la

 //check status of file ('Untracked', 'Modified', 'Changes to be committed')
 git status
 git status --short

 //convert untracked files to stagged
 git add <fileName>
 git add -A

 git status

 git commit -m "<CustomMessage>"

 //add and commit in one line
 git commit -am "<customMessage>"
 
 //view the history of commits for a repository
 git log

 ## Create a new branch
 //create a new branch
 git branch <branch-name>

 //list all branch
 git branch

 //change working branch to the given branch name
 git checkout <branch-name>
 git checkout -b <branch-name>  //create and switched the branch, if it does not exist

### Merge Branches
 //first move to main branch (on which we want to merge)
 git checkout master

 git merge <branch-name>

 //delete branch
 git branch -d <branch-name>

## working with remote repository

 git remote add origin <https://github.com/username/repository.git>
 //NOTE: for this you will need PAT (access token) to your github

### Git Pull from GitHub
 //fetch gets all the change history of a tracked branch/repo from a remote repository
 git fetch origin

 //merge combines the current branch, with a specified branch from remote to local repo
 git merge origin/master

 //But what if you just want to update your local repository, without going through all those steps. pull is a combination of fetch and merge.
 git pull origin

### Git Push to GitHub
 //make changes to local git repository and push to remote repository after commit
 git push origin

### Git Pull branch from GitHub
 //make new branch at remote repo and then
 git pull
 //list all branch (local + remote)
 git branch -a
 //switch to new branch
 git checkout <branchName>
 git pull

### Push branch to GitHub
 //create a new branch in local repo
 git branch -b <branchName>
 //make changes and commit, then
 git push origin <new-created-branch-name>

