
# Git Tutorial Repository

This repository serves as a comprehensive guide to using **Git**. It includes step-by-step instructions for basic Git operations such as cloning repositories, managing branches, and performing pull & push actions with **Remote**.

## Table of Contents

1. [Setting Up Git](#setting-up-git)
2. [Initializing and Cloning Repositories](#initializing-and-cloning-repositories)
6. [Branch Management](#branch-management)
3. [Working with Files (status, add, and commit)](#working-with-files)
5. [Git Stash](#git-stash)
4. [Git Show](#git-show)
7. [Working with Remote Repositories](#working-with-remote-repositories)
8. [Git Pull and Push On Remote](#git-pull-and-push-on-remote)
9. [Gitk (GUI)](#gitk)

<!-- updated table of content
## Table of contents 
- [Git Commands and Their Use](#git-commands-and-their-use)
- [Initialized Git for New Repository](#initialized-git-for-new-repository)
- [Clone Repository from GitHub](#clone-repository-from-github)
- [Status, Add, Commit](#status-add-commit)
- [Git Stash](#git-stash)
  - [Stash Changes](#stash-changes)
  - [List Stashes](#list-stashes)
  - [Apply Stash](#apply-stash)
  - [Pop Stash](#pop-stash)
  - [Drop Stash](#drop-stash)
  - [Clear All Stashes](#clear-all-stashes)
- [Create a New Branch](#create-a-new-branch)
- [Merge Branches](#merge-branches)
- [Working with Remote Repository](#working-with-remote-repository)
  - [Git Pull from GitHub](#git-pull-from-github)
  - [Git Push to GitHub](#git-push-to-github)
  - [Push Branch to GitHub](#push-branch-to-github)
-->

---

## Setting Up Git

Before starting with Git, you need to configure your global Git settings such as your username and email. These settings will be used for all repositories on your local machine unless overridden by repository-specific settings.

### Set Global Username and Email

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

To set username and email for the current repository only (overriding global settings), omit `--global`.

---

## Initializing and Cloning Repositories

### Initialize a New Git Repository

To initialize a new Git repository in the current directory:

```bash
git init
```

### Clone an Existing Remote Repository

To clone a repository from Remote:

```bash
git clone <remote-url>
```

To clone a specific subfolder from the repository:

```bash
git clone <remote-url> <folder-name>
```

This will create a new directory with the repository name, or clone only the specified folder.

### Check Files in the Directory

To view all files, including hidden ones:

```bash
ls -la
```

---

## Branch Management

### Create and Switch Branches

To create a new branch:

```bash
git branch <branch-name>
```

To rename the current branch:

```bash
git branch -m <new-branch-name>
```

To list all branches:

```bash
git branch # Lists only local branches, showing the currently active branch with `*`

git branch -l # Lists local branches only (same as `git branch`)

git brahcn -r # Lists only remote-tracking branches, prefixed by the remote name (e.g., `origin/`)

git branch -a # Lists both local branches and remote-tracking branches
```

To switch to an existing branch:

```bash
git switch <branch-name> 
# or
git checkout <branch-name>
```

To create and switch to a new branch in one step:

```bash
git switch -c <new-branch-name>
# or
git checkout -b <new-branch-name>
```

To create a new branch or reset an existing branch and switch to it.

```bash
git switch -C <new-branch-name>
# or
git checkout -B <new-banch-name>
```

### Merge Branches

To merge changes from another branch into the current branch:

1. Switch to the branch you want to merge into (e.g., `main` or `master`):

   ```bash
   git checkout master
   ```

2. Merge the desired branch:

   ```bash
   git merge <branch-name>
   ```

### Delete a Branch

To delete a branch that is no longer needed:

```bash
git branch -d <branch-name> # only if it has been fully merged to it's target branch
```
```bash
git branch -D <branch-name> # force delete a branch, regardless of whether it has been merged or not
```

---

## Working with Files

### Check the Status of Your Repository

To see the current status of your working directory (untracked, modified, staged files):

```bash
git status
```

For a brief, summary view:

```bash
git status --short
```

### Add Files to Staging Area

To stage a specific file:

```bash
git add <file-name>
```

To stage all changes:

```bash
git add -A
```

After staging, you can check the status again to confirm the changes are staged for commit.

### Commit Changes

To commit the staged changes with a custom message:

```bash
git commit -m "Your commit message"
```

To combine both staging and committing into one step:

```bash
git commit -am "Your commit message"
```

### View Commit History

To view the commit history of the repository:

```bash
git log
```

To view the last `n` commits:

```bash
git log -n <number>
```

Press `q` to exit the log view.

---

## Git Stash

`git stash` is used to **temporarily save changes** in your working directory that are not yet ready to commit. This is useful when you need to switch branches but don’t want to commit partial work.

### 1. Stash Changes

- **Purpose**: Save your local changes (including tracked files) without committing them, but **not** untracked files.
- **Command**: 
  ```bash
  git stash
  ```

- If you want to **stash both tracked and untracked files**, use the `-u` option:
  ```bash
  git stash -u
  ```

### 2. List Stashes

- **Purpose**: See a list of all stashes you've saved.

- **Command**:
  ```bash
  git stash list # list all saved stashes, along with reference ID
  ```

### 3. Apply Stash

- **Purpose**: Reapply the changes from a stash to your working directory.

- **Command**:
  ```bash
  git stash apply [stash@{n}]
  ```
  - `[stash@{n}]` is optional. If not specified, the most recent stash will be applied. If you want to apply a specific stash, use the stash ID from `git stash list`.

### 4. Pop Stash

- **Purpose**: Apply a stash and **remove it** from the stash list.

- **Command**:
  ```bash
  git stash pop [stash@{n}]
  ```

### 5. Drop Stash

- **Purpose**: Delete a stash from the stash list.

- **Command**:
  ```bash
  git stash drop [stash@{n}]
  ```
  Use this to delete a specific stash by its ID.

### 6. Clear All Stashes

- **Purpose**: Remove all stashes.

- **Command**:
  ```bash
  git stash clear
  ```

---

## Git Show

`git show` displays detailed information about a commit, object, or tag. It’s often used to view the content of a specific commit.

- **Purpose**: Show detailed information about a commit or object.

- **Command**:
  ```bash
  git show <commit-hash> # show the commit details, including the commit message, author, date, and the changes made (diff)
  ```

- **Additional Options**:
  ```bash
  git show --stat <commit-hash> # Shows a summary of the files modified in the commit.
  git show --patch <commit-hash> # Shows the patch (diff) introduced by the commit.
  ```

---

## Working with Remote Repositories

When working with remote repositories, you'll often need to add, remove, or update remotes.

### Add a Remote Repository

To link your local repository to a remote:

```bash
git remote add origin <remote-url>
```

You can add multiple remotes with different names, e.g., `origin`, `upstream`, etc.

### Update a Remote URL

To update the URL for a remote repository:

```bash
git remote set-url origin <remote-url>
```

### Remove a Remote Repository

To remove a remote repository:

```bash
git remote rm origin
# or
git remote remove origin
```

### List All Remote Repositories

To view all remotes associated with the repository:

```bash
git remote -v
```

### Fetch Updates from Remote Repository

To fetch all changes from the remote repository without merging:

```bash
git fetch origin # get all the latest changes from the remote repository (e.g., new branches, tags, or updates to existing branches)
```

```bash
git fetch origin <branch-name> # fetch a specific branch (e.g., a feature branch)
```

---

## Git Pull and Push On Remote

### Pull Changes from Remote

To fetch and merge changes from the remote repository into your local branch:

```bash
git pull origin <branch-name>
```

This is equivalent to running `git fetch` followed by `git merge`.

### Push Changes to Remote

To push your local commits to the remote repository:

```bash
git push origin <branch-name>
```

This will push your changes to the corresponding branch on Remote.

### Pull a Branch from Remote

To fetch and checkout a new branch from the remote repository:

```bash
git pull origin <branch-name>
```

### Push a New Branch to Remote

To create a new branch locally, make changes, commit, and push to Remote:

```bash
git branch -b <branch-name> # create a new branch on local
git push origin <branch-name> # push new-branch to remote
```

---

## Gitk

`gitk` is a graphical user interface (GUI) for Git that allows you to visualize and explore the history of a repository.

- **Purpose**: Open a GUI to view commit history, branches, and tags.

- **Command**:
  ```bash
  gitk
  ```
  
- **Usage**: Great for visualizing your commit history and performing complex operations like merges or rebase in a more intuitive way.

---

## Conclusion

This guide covers essential Git commands for interacting with local and remote repositories. By following these steps, you'll be able to effectively manage your projects, collaborate with others, and keep your work organized.
****
