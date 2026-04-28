# Git & GitHub Guide

## About the Instructor

**Chaitanya Sharma**

MERN | Java Backend Developer | Spring Boot | Spring Microservice Pattern | GoLang | Hibernate | PostgresSQL | React js | React Native Expo | LLD

- 📸 Instagram: [https://www.instagram.com/chaitanya.sharrma/](https://www.instagram.com/chaitanya.sharrma/)
- 💻 GitHub: [https://github.com/41chaitanya](https://github.com/41chaitanya)

---

## Table of Contents

1. [Introduction to Git](#introduction-to-git)
2. [Installing Git](#installing-git)
3. [Git Basic Commands](#git-basic-commands)
4. [Git Configuration](#git-configuration)
5. [Working with Repositories](#working-with-repositories)
6. [Git Branching](#git-branching)
7. [Git Log and History](#git-log-and-history)
8. [GitHub Setup](#github-setup)
9. [SSH Key Generation](#ssh-key-generation)
10. [Forking Repositories](#forking-repositories)
11. [Cloning Repositories](#cloning-repositories)
12. [Open Source Contribution Guide](#open-source-contribution-guide)
13. [Best Practices](#best-practices)

---

## Introduction to Git

Git is a distributed version control system that helps developers track changes in their code, collaborate with others, and manage project history efficiently.

### Why Use Git?

- Track changes in your code over time
- Collaborate with multiple developers
- Revert to previous versions if needed
- Work on features independently using branches
- Contribute to open source projects

---

## Installing Git

### Windows
```bash
# Download from: https://git-scm.com/download/win
# Or use chocolatey
choco install git
```

### macOS
```bash
# Using Homebrew
brew install git
```

### Linux (Ubuntu/Debian)
```bash
sudo apt-get update
sudo apt-get install git
```

### Verify Installation
```bash
git --version
```

---

## Git Configuration

Before you start using Git, configure your identity:

```bash
# Set your name
git config --global user.name "Your Name"

# Set your email
git config --global user.email "your.email@example.com"

# Check your configuration
git config --list

# Set default branch name to main
git config --global init.defaultBranch main

# Set default editor (optional)
git config --global core.editor "code --wait"
```

---

## Git Basic Commands

### Initializing a Repository

```bash
# Create a new directory
mkdir my-project
cd my-project

# Initialize Git repository
git init
```

### Checking Status

```bash
# Check the status of your repository
git status
```

### Adding Files

```bash
# Add a specific file
git add filename.txt

# Add all files
git add .

# Add all files with specific extension
git add *.js
```

### Committing Changes

```bash
# Commit with a message
git commit -m "Your commit message"

# Add and commit in one step
git commit -am "Your commit message"
```

### Viewing Changes

```bash
# See unstaged changes
git diff

# See staged changes
git diff --staged

# See changes in a specific file
git diff filename.txt
```

---

## Working with Repositories

### Creating a New Repository

```bash
# Initialize a new repository
git init

# Add files
git add .

# Make first commit
git commit -m "Initial commit"
```

### Connecting to Remote Repository

```bash
# Add remote repository
git remote add origin https://github.com/username/repo-name.git

# Verify remote
git remote -v

# Push to remote
git push -u origin main
```

### Pulling Changes

```bash
# Fetch and merge changes
git pull origin main

# Fetch changes without merging
git fetch origin
```

### Pushing Changes

```bash
# Push to remote repository
git push origin main

# Push all branches
git push --all origin
```

---

## Git Branching

Branches allow you to work on features independently without affecting the main codebase.

```bash
# List all branches
git branch

# Create a new branch
git branch feature-name

# Switch to a branch
git checkout feature-name

# Create and switch to a new branch
git checkout -b feature-name

# Delete a branch
git branch -d feature-name

# Force delete a branch
git branch -D feature-name

# Rename current branch
git branch -m new-branch-name

# Push branch to remote
git push origin feature-name
```

### Merging Branches

```bash
# Switch to the branch you want to merge into
git checkout main

# Merge feature branch into main
git merge feature-name

# Abort a merge in case of conflicts
git merge --abort
```

---

## Git Log and History

### Viewing Commit History

```bash
# View commit history
git log

# View compact log
git log --oneline

# View log with graph
git log --graph --oneline --all

# View log with specific number of commits
git log -n 5

# View log for a specific file
git log filename.txt

# View log with changes
git log -p

# View log with statistics
git log --stat

# View log by author
git log --author="Author Name"

# View log by date
git log --since="2024-01-01"
git log --until="2024-12-31"
```

### Viewing Specific Commits

```bash
# Show details of a specific commit
git show commit-hash

# Show files changed in a commit
git show --name-only commit-hash
```

### Checking Out Previous Commits

```bash
# Checkout a specific commit (detached HEAD state)
git checkout commit-hash

# Return to latest commit
git checkout main
```

### Undoing Changes

```bash
# Unstage a file
git reset HEAD filename.txt

# Discard changes in working directory
git checkout -- filename.txt

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Revert a commit (creates new commit)
git revert commit-hash
```

---

## GitHub Setup

### Creating a GitHub Account

1. Go to [https://github.com](https://github.com)
2. Click "Sign up"
3. Follow the registration process
4. Verify your email address

### Creating a New Repository on GitHub

1. Click the "+" icon in the top right
2. Select "New repository"
3. Enter repository name and description
4. Choose public or private
5. Optionally add README, .gitignore, and license
6. Click "Create repository"

---

## SSH Key Generation

SSH keys provide a secure way to authenticate with GitHub without entering your password every time.

### Step 1: Check for Existing SSH Keys

```bash
# List existing SSH keys
ls -al ~/.ssh
```

### Step 2: Generate New SSH Key

```bash
# Generate SSH key with your GitHub email
ssh-keygen -t ed25519 -C "your.email@example.com"

# For older systems that don't support ed25519
ssh-keygen -t rsa -b 4096 -C "your.email@example.com"

# Press Enter to accept default file location
# Enter a secure passphrase (optional but recommended)
```

### Step 3: Add SSH Key to SSH Agent

```bash
# Start the SSH agent
eval "$(ssh-agent -s)"

# Add your SSH private key to the agent
ssh-add ~/.ssh/id_ed25519

# For RSA key
ssh-add ~/.ssh/id_rsa
```

### Step 4: Copy SSH Key to Clipboard

```bash
# macOS
pbcopy < ~/.ssh/id_ed25519.pub

# Linux (requires xclip)
xclip -selection clipboard < ~/.ssh/id_ed25519.pub

# Windows (Git Bash)
clip < ~/.ssh/id_ed25519.pub

# Or manually display and copy
cat ~/.ssh/id_ed25519.pub
```

### Step 5: Add SSH Key to GitHub

1. Go to GitHub Settings: [https://github.com/settings/keys](https://github.com/settings/keys)
2. Click "New SSH key"
3. Give it a descriptive title (e.g., "My Laptop")
4. Paste your SSH key
5. Click "Add SSH key"

### Step 6: Test SSH Connection

```bash
# Test your SSH connection
ssh -T git@github.com

# You should see: "Hi username! You've successfully authenticated..."
```

### Using SSH with Git

```bash
# Clone using SSH
git clone git@github.com:username/repo-name.git

# Change existing repository to use SSH
git remote set-url origin git@github.com:username/repo-name.git
```

---

## Forking Repositories

Forking creates a personal copy of someone else's repository under your GitHub account.

### How to Fork a Repository

1. Navigate to the repository you want to fork
2. Click the "Fork" button in the top right corner
3. Select your account as the destination
4. Wait for GitHub to create the fork

### Syncing Your Fork

```bash
# Add the original repository as upstream
git remote add upstream https://github.com/original-owner/repo-name.git

# Verify remotes
git remote -v

# Fetch changes from upstream
git fetch upstream

# Merge upstream changes into your main branch
git checkout main
git merge upstream/main

# Push updates to your fork
git push origin main
```

---

## Cloning Repositories

Cloning creates a local copy of a repository on your machine.

### Clone via HTTPS

```bash
# Clone a repository
git clone https://github.com/username/repo-name.git

# Clone into a specific directory
git clone https://github.com/username/repo-name.git my-folder

# Clone a specific branch
git clone -b branch-name https://github.com/username/repo-name.git
```

### Clone via SSH

```bash
# Clone using SSH (requires SSH key setup)
git clone git@github.com:username/repo-name.git
```

### Clone with Depth (Shallow Clone)

```bash
# Clone only recent history (faster for large repos)
git clone --depth 1 https://github.com/username/repo-name.git
```

---

## Open Source Contribution Guide

### Step-by-Step Contribution Process

#### 1. Find a Project

- Browse GitHub topics and trending repositories
- Look for repositories with "good first issue" or "beginner-friendly" labels
- Check the project's CONTRIBUTING.md file

#### 2. Fork the Repository

- Click the "Fork" button on the project's GitHub page
- This creates a copy under your account

#### 3. Clone Your Fork

```bash
git clone git@github.com:your-username/repo-name.git
cd repo-name
```

#### 4. Set Up Upstream Remote

```bash
# Add original repository as upstream
git remote add upstream git@github.com:original-owner/repo-name.git

# Verify remotes
git remote -v
```

#### 5. Create a New Branch

```bash
# Create and switch to a new branch
git checkout -b feature/your-feature-name

# Or for bug fixes
git checkout -b fix/bug-description
```

#### 6. Make Your Changes

- Write clean, well-documented code
- Follow the project's coding standards
- Test your changes thoroughly

#### 7. Commit Your Changes

```bash
# Stage your changes
git add .

# Commit with a descriptive message
git commit -m "Add: Brief description of your changes"
```

### Commit Message Conventions

```bash
# Feature addition
git commit -m "Add: User authentication feature"

# Bug fix
git commit -m "Fix: Login button not responding"

# Documentation
git commit -m "Docs: Update installation instructions"

# Refactoring
git commit -m "Refactor: Optimize database queries"

# Testing
git commit -m "Test: Add unit tests for auth module"
```

#### 8. Push to Your Fork

```bash
# Push your branch to your fork
git push origin feature/your-feature-name
```

#### 9. Create a Pull Request

1. Go to your fork on GitHub
2. Click "Compare & pull request"
3. Fill in the PR template:
   - Clear title describing the change
   - Detailed description of what and why
   - Reference any related issues (#issue-number)
4. Click "Create pull request"

#### 10. Respond to Feedback

- Be open to suggestions and code reviews
- Make requested changes promptly
- Push additional commits to the same branch
- Engage respectfully with maintainers

#### 11. Keep Your Fork Updated

```bash
# Fetch upstream changes
git fetch upstream

# Switch to main branch
git checkout main

# Merge upstream changes
git merge upstream/main

# Push to your fork
git push origin main
```

---

## Best Practices

### Commit Best Practices

1. **Write Clear Commit Messages**
   - Use present tense ("Add feature" not "Added feature")
   - Keep first line under 50 characters
   - Add detailed description if needed

2. **Commit Often**
   - Make small, logical commits
   - Each commit should represent one logical change
   - Don't commit broken code

3. **Use Meaningful Branch Names**
   ```bash
   # Good
   feature/user-authentication
   fix/login-bug
   docs/readme-update
   
   # Bad
   test
   new-branch
   asdf
   ```

### Branching Best Practices

1. **Keep Main Branch Clean**
   - Never commit directly to main
   - Always work on feature branches
   - Merge only tested and reviewed code

2. **Branch Naming Conventions**
   - `feature/` - New features
   - `fix/` - Bug fixes
   - `docs/` - Documentation changes
   - `refactor/` - Code refactoring
   - `test/` - Adding tests

3. **Delete Merged Branches**
   ```bash
   # Delete local branch
   git branch -d feature-name
   
   # Delete remote branch
   git push origin --delete feature-name
   ```

### Collaboration Best Practices

1. **Pull Before You Push**
   ```bash
   git pull origin main
   git push origin main
   ```

2. **Resolve Conflicts Carefully**
   - Understand both changes before resolving
   - Test after resolving conflicts
   - Ask for help if unsure

3. **Use .gitignore**
   - Ignore build files, dependencies, and sensitive data
   - Use templates from [gitignore.io](https://www.toptal.com/developers/gitignore)

### Code Review Best Practices

1. **As a Contributor**
   - Keep PRs small and focused
   - Provide context in PR description
   - Respond to feedback professionally
   - Test your changes thoroughly

2. **As a Reviewer**
   - Be constructive and respectful
   - Explain the "why" behind suggestions
   - Approve when ready, request changes when needed

### Security Best Practices

1. **Never Commit Sensitive Data**
   - API keys, passwords, tokens
   - Use environment variables
   - Add sensitive files to .gitignore

2. **Review Before Committing**
   ```bash
   # Check what you're about to commit
   git diff --staged
   ```

3. **Use SSH Keys**
   - More secure than HTTPS
   - No password needed for each push

### Documentation Best Practices

1. **Keep README Updated**
   - Clear project description
   - Installation instructions
   - Usage examples
   - Contribution guidelines

2. **Comment Your Code**
   - Explain complex logic
   - Document functions and classes
   - Keep comments up to date

3. **Write Good PR Descriptions**
   - What changes were made
   - Why the changes were necessary
   - How to test the changes

---

## Common Git Commands Cheat Sheet

```bash
# Configuration
git config --global user.name "Name"
git config --global user.email "email@example.com"

# Repository
git init
git clone <url>

# Status & Changes
git status
git diff
git diff --staged

# Adding & Committing
git add <file>
git add .
git commit -m "message"
git commit -am "message"

# Branching
git branch
git branch <name>
git checkout <branch>
git checkout -b <branch>
git merge <branch>
git branch -d <branch>

# Remote
git remote add origin <url>
git remote -v
git push origin <branch>
git pull origin <branch>
git fetch origin

# History
git log
git log --oneline
git log --graph --oneline --all
git show <commit>

# Undo
git reset HEAD <file>
git checkout -- <file>
git reset --soft HEAD~1
git reset --hard HEAD~1
git revert <commit>

# Stash
git stash
git stash list
git stash apply
git stash pop
git stash drop
```

---

## Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [Pro Git Book](https://git-scm.com/book/en/v2)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [First Contributions](https://github.com/firstcontributions/first-contributions)
- [How to Contribute to Open Source](https://opensource.guide/how-to-contribute/)

---

## Connect with Chaitanya Sharma

- 📸 Instagram: [@chaitanya.sharrma](https://www.instagram.com/chaitanya.sharrma/)
- 💻 GitHub: [@41chaitanya](https://github.com/41chaitanya)

Happy Coding! 🚀
