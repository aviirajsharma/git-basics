# Git and GitHub Basics

A comprehensive guide covering essential Git commands and GitHub concepts for quick revision.

---

## 📚 Table of Contents
1. [What is Git?](#what-is-git)
2. [What is GitHub?](#what-is-github)
3. [Git Installation](#git-installation)
4. [Git Configuration](#git-configuration)
5. [Basic Git Commands](#basic-git-commands)
6. [Working with GitHub](#working-with-github)
7. [Branching and Merging](#branching-and-merging)
8. [Git Log and History](#git-log-and-history)
9. [Undoing Changes](#undoing-changes)
10. [Working with Remote Repositories](#working-with-remote-repositories)
11. [Stashing Changes](#stashing-changes)
12. [Useful Git Tips](#useful-git-tips)

---

## 🚀 What is Git?
- **Git** is a distributed version control system used to track changes in source code during software development.
- It allows multiple developers to work on the same project without interfering with each other.

---

## 🌐 What is GitHub?
- **GitHub** is a web-based platform for version control and collaboration, built on top of Git.
- It allows you to store Git repositories online, collaborate with others, and manage projects.

---

## ⚙️ Git Installation
### Install Git:
- **Windows**: [Download Git for Windows](https://git-scm.com/download/win)
- **macOS**: `brew install git`
- **Linux**: `sudo apt install git` (Debian/Ubuntu)

### Verify Installation:
```bash
git --version
```

---

## 🛠️ Git Configuration
Set your username and email (needed for commits):

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
```

Check all configurations:
```bash
git config --list
```

---

## 📂 Basic Git Commands
### Initialize a Git Repository
```bash
git init
```

### Clone an Existing Repository
```bash
git clone <repository_url>
```

### Check the Status of Files
```bash
git status
```

### Add Files to Staging Area
```bash
git add <file_name>
# Add all files
git add .
```

### Commit Changes
```bash
git commit -m "Commit message"
```

### View Remote URL
```bash
git remote -v
```

---

## 🌟 Working with GitHub
### Connect Local Repo to GitHub
```bash
git remote add origin <repository_url>
```

### Push Changes to GitHub
```bash
git push -u origin main
```

### Pull Changes from GitHub
```bash
git pull origin main
```

### Fork and Clone Repositories
- **Fork** a repository on GitHub UI.
- **Clone** the forked repo:
```bash
git clone <forked_repo_url>
```

---

## 🌿 Branching and Merging
### Create a New Branch
```bash
git branch <branch_name>
```

### Switch to a Branch
```bash
git checkout <branch_name>
```

### Create and Switch to a Branch
```bash
git checkout -b <branch_name>
```

### Merge a Branch
```bash
git checkout main
git merge <branch_name>
```

### Delete a Branch
```bash
git branch -d <branch_name>
```

---

## 📜 Git Log and History
### View Commit History
```bash
git log
```

### One-line Log
```bash
git log --oneline
```

### Graphical Log
```bash
git log --oneline --graph --all
```

---

## 🔄 Undoing Changes
### Unstage a File
```bash
git reset <file_name>
```

### Amend Last Commit
```bash
git commit --amend
```

### Discard Changes in Working Directory
```bash
git checkout -- <file_name>
```

---

## 🌍 Working with Remote Repositories
### Add Remote Repository
```bash
git remote add origin <repository_url>
```

### Remove Remote Repository
```bash
git remote remove origin
```

### Rename Remote Repository
```bash
git remote rename <old_name> <new_name>
```

---

## 💾 Stashing Changes
### Stash Current Changes
```bash
git stash
```

### Apply Stashed Changes
```bash
git stash apply
```

### View Stashes
```bash
git stash list
```

### Drop a Stash
```bash
git stash drop <stash_id>
```

---

## 💡 Useful Git Tips
- **Check Differences:**
  ```bash
  git diff
  ```
- **Short Git Status:**
  ```bash
  git status -s
  ```
- **Show Detailed Commit:**
  ```bash
  git show <commit_hash>
  ```

---

## 🎯 Conclusion
This `README.md` provides essential Git and GitHub commands for everyday use. Keep it handy for quick revisions and reference during development!

