# Complete Git and GitHub Guide

## Table of Contents
1. [What is Git?](#what-is-git)
2. [What is GitHub?](#what-is-github)
3. [Installation](#installation)
4. [Basic Git Configuration](#basic-git-configuration)
5. [Git Basics](#git-basics)
6. [Working with Repositories](#working-with-repositories)
7. [Branching and Merging](#branching-and-merging)
8. [Remote Repositories](#remote-repositories)
9. [GitHub Workflow](#github-workflow)
10. [Advanced Git Commands](#advanced-git-commands)
11. [Git Best Practices](#git-best-practices)
12. [Troubleshooting Common Issues](#troubleshooting-common-issues)

---

## What is Git?

Git is a distributed version control system that tracks changes in files and coordinates work among multiple people. It allows you to:
- Track changes in your code over time
- Collaborate with others on the same project
- Revert to previous versions if needed
- Work on different features simultaneously through branching

## What is GitHub?

GitHub is a cloud-based hosting service for Git repositories. It provides:
- Remote storage for your Git repositories
- Collaboration tools (issues, pull requests, project boards)
- Social coding features (following, starring repositories)
- CI/CD integration and deployment tools

---

## Installation

### Windows
```bash
# Download from https://git-scm.com/download/win
# Or using Chocolatey
choco install git

# Or using winget
winget install Git.Git
```

### macOS
```bash
# Using Homebrew
brew install git

# Or download from https://git-scm.com/download/mac
```

### Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install git
```

### Verify Installation
```bash
git --version
```

---

## Basic Git Configuration

### Set Your Identity
```bash
# Set your name (required for commits)
git config --global user.name "Your Name"

# Set your email (required for commits)
git config --global user.email "your.email@example.com"
```

### Other Useful Configurations
```bash
# Set default text editor
git config --global core.editor "code --wait"  # For VS Code
git config --global core.editor "vim"          # For Vim

# Set default branch name
git config --global init.defaultBranch main

# Enable colored output
git config --global color.ui auto

# View all configurations
git config --list

# View specific configuration
git config user.name
```

---

## Git Basics

### Initialize a Repository
```bash
# Create a new Git repository in current directory
git init

# Create a new directory and initialize Git
git init my-project
cd my-project
```

### Check Repository Status
```bash
# Show the working tree status
git status

# Show status in short format
git status -s
```

### Staging Changes
```bash
# Add specific file to staging area
git add filename.txt

# Add all files in current directory
git add .

# Add all files with specific extension
git add *.js

# Add all files in a directory
git add src/

# Interactive staging
git add -i

# Add parts of a file (patch mode)
git add -p filename.txt
```

### Committing Changes
```bash
# Commit staged changes with message
git commit -m "Your commit message"

# Commit with detailed message (opens editor)
git commit

# Add and commit in one step
git commit -am "Message for all tracked files"

# Amend the last commit
git commit --amend -m "New commit message"
```

### Viewing History
```bash
# Show commit history
git log

# Show compact history
git log --oneline

# Show history with graph
git log --graph --oneline --all

# Show specific number of commits
git log -5

# Show commits by author
git log --author="Author Name"

# Show commits in date range
git log --since="2023-01-01" --until="2023-12-31"
```

### Viewing Changes
```bash
# Show changes in working directory
git diff

# Show changes in staging area
git diff --staged

# Show changes between commits
git diff commit1 commit2

# Show changes in specific file
git diff filename.txt
```

---

## Working with Repositories

### Cloning Repositories
```bash
# Clone a repository
git clone https://github.com/username/repository.git

# Clone to specific directory
git clone https://github.com/username/repository.git my-folder

# Clone specific branch
git clone -b branch-name https://github.com/username/repository.git

# Shallow clone (recent history only)
git clone --depth 1 https://github.com/username/repository.git
```

### Ignoring Files
Create a `.gitignore` file in your repository root:
```gitignore
# Ignore node_modules directory
node_modules/

# Ignore all .log files
*.log

# Ignore specific file
config/secret.txt

# Ignore all files in temp directory
temp/*

# But don't ignore temp/.gitkeep
!temp/.gitkeep

# Ignore files only in root directory
/file-in-root.txt

# Ignore all .env files in any directory
**/.env
```

### Removing Files
```bash
# Remove file from working directory and staging area
git rm filename.txt

# Remove file only from staging area (keep in working directory)
git rm --cached filename.txt

# Remove directory recursively
git rm -r directory-name/

# Force remove (if file is modified)
git rm -f filename.txt
```

---

## Branching and Merging

### Working with Branches
```bash
# List all branches
git branch

# List all branches (including remote)
git branch -a

# Create new branch
git branch new-feature

# Switch to branch
git checkout new-feature

# Create and switch to new branch
git checkout -b new-feature

# Switch to branch (newer syntax)
git switch new-feature

# Create and switch to new branch (newer syntax)
git switch -c new-feature

# Rename current branch
git branch -m new-name

# Rename specific branch
git branch -m old-name new-name

# Delete branch
git branch -d branch-name

# Force delete branch (unmerged changes)
git branch -D branch-name
```

### Merging Branches
```bash
# Merge branch into current branch
git merge feature-branch

# Merge with no fast-forward (create merge commit)
git merge --no-ff feature-branch

# Merge with squash (combine all commits into one)
git merge --squash feature-branch

# Abort merge if conflicts occur
git merge --abort
```

### Resolving Merge Conflicts
When conflicts occur:
1. Git marks conflicted files
2. Edit files to resolve conflicts
3. Remove conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
4. Stage resolved files: `git add filename.txt`
5. Complete merge: `git commit`

```bash
# Show files with conflicts
git status

# Use merge tool
git mergetool

# Show conflict diff
git diff
```

---

## Remote Repositories

### Adding Remotes
```bash
# Add remote repository
git remote add origin https://github.com/username/repository.git

# List remotes
git remote -v

# Show remote details
git remote show origin

# Rename remote
git remote rename origin upstream

# Remove remote
git remote remove origin

# Change remote URL
git remote set-url origin https://github.com/username/new-repository.git
```

### Fetching and Pulling
```bash
# Fetch changes from remote (doesn't merge)
git fetch origin

# Fetch all remotes
git fetch --all

# Pull changes (fetch + merge)
git pull origin main

# Pull with rebase instead of merge
git pull --rebase origin main

# Pull specific branch
git pull origin feature-branch
```

### Pushing Changes
```bash
# Push to remote repository
git push origin main

# Push new branch to remote
git push -u origin new-feature

# Push all branches
git push --all origin

# Push tags
git push --tags origin

# Force push (dangerous!)
git push --force origin main

# Safer force push
git push --force-with-lease origin main

# Delete remote branch
git push origin --delete branch-name
```

---

## GitHub Workflow

### Creating a Repository on GitHub
1. Go to GitHub and click "New repository"
2. Name your repository
3. Choose public or private
4. Initialize with README (optional)
5. Click "Create repository"

### Connecting Local Repository to GitHub
```bash
# If repository exists locally
git remote add origin https://github.com/username/repository.git
git branch -M main
git push -u origin main

# If starting from GitHub repository
git clone https://github.com/username/repository.git
```

### Working with Issues
```bash
# Reference issue in commit message
git commit -m "Fix login bug - closes #123"

# Commit messages that close issues:
# "fixes #123", "closes #123", "resolves #123"
```

### Pull Requests Workflow
1. Fork the repository (if contributing to others' projects)
2. Clone your fork: `git clone https://github.com/yourusername/repository.git`
3. Create feature branch: `git checkout -b feature-name`
4. Make changes and commit: `git commit -m "Add new feature"`
5. Push branch: `git push origin feature-name`
6. Create pull request on GitHub
7. Discuss and make changes if needed
8. Merge pull request when approved

### GitHub Pages
```bash
# Deploy to GitHub Pages (gh-pages branch)
git checkout --orphan gh-pages
git rm -rf .
echo "Hello GitHub Pages" > index.html
git add index.html
git commit -m "Initial GitHub Pages commit"
git push origin gh-pages
```

---

## Advanced Git Commands

### Stashing Changes
```bash
# Stash current changes
git stash

# Stash with message
git stash push -m "Work in progress on feature X"

# List stashes
git stash list

# Apply most recent stash
git stash apply

# Apply specific stash
git stash apply stash@{2}

# Apply and remove stash
git stash pop

# Drop specific stash
git stash drop stash@{1}

# Clear all stashes
git stash clear

# Stash untracked files too
git stash -u
```

### Rebasing
```bash
# Rebase current branch onto main
git rebase main

# Interactive rebase (last 3 commits)
git rebase -i HEAD~3

# Continue rebase after resolving conflicts
git rebase --continue

# Abort rebase
git rebase --abort

# Skip problematic commit during rebase
git rebase --skip
```

### Cherry Picking
```bash
# Apply specific commit to current branch
git cherry-pick commit-hash

# Cherry pick without committing
git cherry-pick -n commit-hash

# Cherry pick a range of commits
git cherry-pick commit1..commit2
```

### Reset and Revert
```bash
# Soft reset (keep changes staged)
git reset --soft HEAD~1

# Mixed reset (keep changes unstaged) - default
git reset HEAD~1

# Hard reset (discard all changes)
git reset --hard HEAD~1

# Reset to specific commit
git reset --hard commit-hash

# Revert a commit (creates new commit)
git revert commit-hash

# Revert merge commit
git revert -m 1 merge-commit-hash
```

### Tagging
```bash
# Create lightweight tag
git tag v1.0

# Create annotated tag
git tag -a v1.0 -m "Version 1.0 release"

# Tag specific commit
git tag -a v1.0 commit-hash -m "Version 1.0"

# List tags
git tag

# List tags with pattern
git tag -l "v1.*"

# Show tag details
git show v1.0

# Delete tag
git tag -d v1.0

# Delete remote tag
git push origin --delete v1.0

# Push tags to remote
git push origin --tags
```

### Searching and Debugging
```bash
# Search for text in files
git grep "search-term"

# Search in specific files
git grep "search-term" -- "*.js"

# Show who changed each line of a file
git blame filename.txt

# Find commit that introduced a bug (binary search)
git bisect start
git bisect bad          # Current commit is bad
git bisect good v1.0    # v1.0 was good
# Git will checkout commits for you to test
git bisect good         # If current commit is good
git bisect bad          # If current commit is bad
git bisect reset        # When done
```

---

## Git Best Practices

### Commit Messages
- Use present tense ("Add feature" not "Added feature")
- Keep first line under 50 characters
- Use imperative mood ("Fix bug" not "Fixes bug")
- Reference issues when relevant

**Good commit message format:**
```
Short summary (50 chars or less)

More detailed description if needed. Wrap at 72 characters.
Explain what and why, not how.

- Bullet points are okay
- Use hyphens or asterisks

Fixes #123
```

### Branch Naming
- Use descriptive names: `feature/user-authentication`
- Use prefixes: `feature/`, `bugfix/`, `hotfix/`
- Use lowercase and hyphens: `feature/add-payment-system`

### Workflow Recommendations
1. **Always pull before starting work**: `git pull origin main`
2. **Work on feature branches**: Don't commit directly to main
3. **Make small, focused commits**: One logical change per commit
4. **Test before committing**: Ensure code works
5. **Use meaningful commit messages**: Future you will thank you
6. **Regularly push to remote**: Don't lose work

### Repository Structure
```
project/
├── .gitignore
├── README.md
├── LICENSE
├── src/
├── tests/
├── docs/
└── scripts/
```

---

## Troubleshooting Common Issues

### Common Problems and Solutions

**1. "Permission denied (publickey)" Error:**
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Add to SSH agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy public key to GitHub
cat ~/.ssh/id_ed25519.pub
# Paste in GitHub Settings > SSH Keys
```

**2. Committed to Wrong Branch:**
```bash
# Move last commit to new branch
git branch new-branch
git reset HEAD~1 --hard
git checkout new-branch
```

**3. Undo Last Commit (Keep Changes):**
```bash
git reset --soft HEAD~1
```

**4. Discard All Local Changes:**
```bash
git reset --hard HEAD
git clean -fd  # Remove untracked files
```

**5. Change Last Commit Message:**
```bash
git commit --amend -m "New message"
```

**6. Merge Conflicts:**
```bash
# See conflicted files
git status

# After resolving conflicts
git add .
git commit
```

**7. Accidentally Deleted File:**
```bash
# Restore file from last commit
git checkout HEAD -- filename.txt

# Restore all files
git checkout HEAD -- .
```

**8. View File from Different Commit:**
```bash
git show commit-hash:path/to/file.txt
```

**9. Find Lost Commits:**
```bash
# Show reference log
git reflog

# Recover lost commit
git checkout lost-commit-hash
git branch recovery-branch
```

**10. Remove File from History:**
```bash
# Remove file from all history (dangerous!)
git filter-branch --force --index-filter \
'git rm --cached --ignore-unmatch path/to/file' \
--prune-empty --tag-name-filter cat -- --all
```

---

## Useful Git Aliases

Add these to your `.gitconfig` file or use `git config --global alias.alias-name "command"`:

```bash
# Shortcuts
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit

# Useful aliases
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
git config --global alias.tree 'log --graph --pretty=format:"%h %s" --all'
git config --global alias.amend 'commit --amend --no-edit'
```

---

## Resources and Further Learning

### Official Documentation
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Documentation](https://docs.github.com/)

### Interactive Learning
- [Learn Git Branching](https://learngitbranching.js.org/)
- [GitHub Skills](https://skills.github.com/)

### Cheat Sheets
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Interactive Git Cheat Sheet](https://ndpsoftware.com/git-cheatsheet.html)

### Books
- "Pro Git" by Scott Chacon and Ben Straub (free online)
- "Git Pocket Guide" by Richard E. Silverman

---

## Quick Reference

### Essential Commands
```bash
git init                    # Initialize repository
git clone <url>            # Clone repository
git add <file>             # Stage changes
git commit -m "message"    # Commit changes
git push origin main       # Push to remote
git pull origin main       # Pull from remote
git status                 # Check status
git log                    # View history
git branch                 # List branches
git checkout <branch>      # Switch branch
git merge <branch>         # Merge branch
```

### Emergency Commands
```bash
git stash                  # Save work temporarily
git reset --hard HEAD      # Discard all changes
git checkout -- <file>     # Discard file changes
git reflog                 # Find lost commits
git commit --amend         # Fix last commit
```

Remember: Git is powerful but can be dangerous. Always backup important work and be careful with commands that rewrite history (`reset --hard`, `rebase`, `filter-branch`) especially when working with shared repositories!

Connect on X : [Aviraj Sharma](https://x.com/aviiraj_sharma)

Connect on LinkedIn : [Aviraj Sharma](https://www.linkedin.com/in/avirajsharma/)


