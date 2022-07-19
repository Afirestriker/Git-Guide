# Hello World
Hello World repository for Git tutorial
This is an example repository for the Git tutorial

This repository includes steps for Git pull & push with GitHub

> # Git commands and their use
 //global -> set the username and email for every repository on your computer  
 //remove global to set username and email for current repo only.  
 - git config --global user.name "author/userName"   
 - git config --global user.email "email-registered-with-GitHub"  

 //cd into the folder where you want to create new or clone project repository   

 ## Initialized Git for new repository
 //to initialized git  
 - git init  

 ## Clone repository from GitHub
 //to clone git, these will add new directory in current folder with the repository name  
 - git clone https://github.com/username/repository.git  
  
 //to clone specific folder inside repository add folder name at the end of above command with space  
 - git clone https://github.com/username/repository.git \<folderName>  
 
 
 //check all file including hidden  
 - ls -la  

 ## Status, Add, Commit
 //check status of file ('Untracked', 'Modified', 'Changes to be committed')  
 - git status  
 - git status --short  
 
 //convert untracked files to stagged  
 - git add \<fileName>  
 - git add -A  

 //After adding, the status should have been "To be committed"  
 - git status  

 //Convert Stagged/added file to commit (save point)  
 - git commit -m "CustomMessage"  

 //Combining Add & Commit in one command  
 - git commit -am "customMessage"  
 
 //view the log history of commits for a repository (all log or last n log)  
 - git log  
 - git log -n \<number>  
 
 ## Create a new branch  
 //create a new branch  
 - git branch \<branch-name>  

 //rename a branch (rename current branch)  
 git branch -m \<new-branch-name>
 
 //list all branch  
 - git branch  

 //change working branch to the given branch name  
 - git checkout \<branch-name>  
 
 //create and switched the branch, if it does not exist  
 - git checkout -b \<branch-name>  

### Merge Branches  
 //first move to main branch (on which we want to merge)  
 - git checkout master  

 - git merge \<branch-name>      //name of the branch which we want to merge  

 //delete branch  
 - git branch -d \<branch-name>  

# working with remote repository  
 //NOTE: for this you will need PAT (access token) to your GitHub (if using Git Bash)  
 //Recommend: To use Visual Studio - add GitHub to Visual Studio
 
 - git remote add origin https://github.com/username/repository.git  
   //NOTE: here name "origin" can be any other name, you can add multiple remote with different name and update or remove them using below command
 
 //update git remote value for particualar remote
 - git remote set-url origin https://github.com/username/repository.git  
 
 //remove git remote for particular value
 - git remote remove origin
 - git remote rm origin
  
 //check all remote name & their value i.e. to which directory the particular remote point to for fetch/pull and push command  
 - git remote -v  

 //fetch gets all the change history of a tracked branch/repo from a remote repository  
 - git fetch origin  

## Git Pull from GitHub  
 //merge combines the current branch, with a specified branch from remote to local repository  
 - git merge origin/master  

 //But what if you just want to update your local repository, without going through all those steps. pull is a combination of fetch and merge.  
 - git pull origin  

## Git Push to GitHub  
 //make changes to local git repository and push to remote repository after commit  
 - git push origin  

### Git Pull branch from GitHub  
 //make new branch at remote repo and then  
 - git pull  
 
 //list all branch (local + remote)  
 - git branch -a  
   
 //switch to new branch  
 - git checkout \<branchName>  
 - git pull  

### Push branch to GitHub  
 //create a new branch in local repo  
 - git branch -b \<branchName>  
 
 //make changes and commit, then  
 - git push origin \<new-created-branch-name>  

