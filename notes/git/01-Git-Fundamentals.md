# Git Fundamentals

## Overview

This document summarizes the Git fundamentals I learned while setting up and maintaining my `ai-engineering-journey` repository.

It covers the complete workflow I have practiced so far, from creating a local repository to pushing commits to GitHub.

---

## 1. What Is Git?

Git is a version control system.

It tracks changes made to a project and allows developers to:

- keep a history of their work
- understand what changed
- return to an earlier version
- work safely on new features
- collaborate with other developers

Git works locally on a computer.

GitHub is an online platform used to store, share, and collaborate on Git repositories.

### Git and GitHub Are Different

```text
Git     = version control system
GitHub  = online platform for Git repositories
```

A project can use Git without GitHub, but GitHub provides a remote location where the repository can be stored and shared.

---

## 2. Repository

A repository, or repo, is a project that Git tracks.

Example:

```text
ai-engineering-journey/
```

A normal folder becomes a Git repository after running:

```bash
git init
```

After initialization, Git begins tracking the project through its internal `.git` directory.

---

## 3. The `.git` Directory

When `git init` is executed, Git creates a hidden directory named:

```text
.git
```

This directory stores Git's internal information, including:

- commit history
- branches
- configuration
- references
- internal Git objects

The `.git` directory is hidden so that it is not accidentally modified or deleted.

Deleting `.git` does not delete the project files, but it removes the Git history and turns the project back into a normal folder.

---

## 4. Creating a Repository

One method is to create the folder first:

```bash
mkdir ai-engineering-journey
cd ai-engineering-journey
git init
```

Another method is:

```bash
git init ai-engineering-journey
```

The second command creates the folder and initializes Git inside it.

The first approach makes each step easier to understand:

- `mkdir` creates the folder
- `cd` enters the folder
- `git init` creates the Git repository

---

## 5. Git Configuration

Git uses configuration values such as the author's name and email.

Global configuration applies to all repositories created by the current computer user.

```bash
git config --global user.name "maig"
git config --global user.email "your-email@example.com"
```

The default branch can also be configured globally:

```bash
git config --global init.defaultBranch main
```

Configuration values and their source files can be viewed with:

```bash
git config --list --show-origin
```

---

## 6. Branches

A branch is an independent development line inside a repository.

The main branch is usually named:

```text
main
```

New features can be developed in separate branches without immediately changing the stable code.

Example:

```text
main
  └── feature-login
```

After the feature is completed and tested, it can later be merged into `main`.

### `master` and `main`

`master` and `main` serve the same technical purpose as branch names.

Older Git configurations often use:

```text
master
```

Modern repositories usually use:

```text
main
```

The current branch can be renamed with:

```bash
git branch -M main
```

To make all newly created repositories use `main` by default:

```bash
git config --global init.defaultBranch main
```

---

## 7. The Three Main Git Areas

The Git workflow can be understood through three main areas.

### 7.1 Working Directory

The Working Directory contains the current project files.

When a file is created, edited, renamed, moved, or deleted, the change first appears here.

### 7.2 Staging Area

The Staging Area contains changes selected for the next commit.

Changes are added to the Staging Area with:

```bash
git add .
```

A specific file can be staged with:

```bash
git add README.md
```

### 7.3 Git History

Git History contains the saved commits.

A commit is a permanent snapshot of the staged changes at a specific moment.

```text
Working Directory
        ↓ git add
Staging Area
        ↓ git commit
Git History
```

---

## 8. Checking Repository Status

The current state of the repository can be checked with:

```bash
git status
```

This command can show:

- modified files
- untracked files
- staged changes
- the current branch
- whether the local branch is ahead of or behind the remote branch

When Git displays:

```text
nothing to commit, working tree clean
```

it means there are no uncommitted changes.

---

## 9. Staging Changes

To stage all current changes:

```bash
git add .
```

To stage one specific file:

```bash
git add README.md
```

`git add` does not permanently save the changes.

It only prepares them for the next commit.

---

## 10. Commits

A commit is a saved snapshot of the project at a specific moment.

Example:

```bash
git commit -m "Initial learning notes"
```

A commit helps developers:

- track progress
- understand what changed
- return to an earlier version
- organize project history

A good commit message should briefly explain the change.

### Commit Message Convention

This repository uses structured commit messages.

Examples:

```text
docs: add variables notes
docs: improve OOP explanations
feat: add calculator project
fix: correct code example
refactor: reorganize project structure
```

Common prefixes:

- `docs:` documentation changes
- `feat:` new functionality
- `fix:` bug fixes
- `refactor:` code restructuring
- `test:` test-related changes
- `style:` formatting changes

Example used for reorganizing the learning notes:

```bash
git commit -m "docs: reorganize learning notes structure"
```

---

## 11. Viewing Commit History

The commit history can be viewed with:

```bash
git log
```

This command shows information such as:

- commit identifier
- author
- date
- commit message

The log makes it possible to review how the project has changed over time.

---

## 12. Remote Repository

A remote repository is an online version of a local Git repository.

The `ai-engineering-journey` repository is hosted on GitHub.

The remote repository was connected with:

```bash
git remote add origin git@github.com:imaige/ai-engineering-journey.git
```

Configured remotes can be checked with:

```bash
git remote -v
```

### What Is `origin`?

`origin` is the conventional name of the main remote repository.

It is only a short local name that points to the GitHub repository URL.

```text
origin → git@github.com:imaige/ai-engineering-journey.git
```

---

## 13. SSH Authentication

SSH allows Git to communicate securely with GitHub without entering a username and password for every push.

Because the default SSH port `22` was unavailable, GitHub SSH was configured through port `443`.

The SSH configuration file contains:

```text
Host github.com
    HostName ssh.github.com
    User git
    Port 443
    IdentityFile ~/.ssh/id_ed25519
```

This configuration means:

- commands can continue using `github.com`
- the real SSH connection goes to `ssh.github.com`
- the connection uses port `443`
- the private key is read from `~/.ssh/id_ed25519`

The connection can be tested with:

```bash
ssh -T git@github.com
```

---

## 14. First Push to GitHub

The local `main` branch was pushed to GitHub with:

```bash
git push -u origin main
```

Explanation:

- `git push` sends local commits to the remote repository
- `origin` is the remote repository name
- `main` is the branch name
- `-u` creates an upstream tracking connection

After the upstream is configured, future pushes can be performed with:

```bash
git push
```

---

## 15. Upstream Branch Tracking

An upstream branch connects a local branch to its corresponding remote branch.

In this repository:

```text
local main → origin/main
```

The upstream relationship was created with:

```bash
git push -u origin main
```

Because this connection exists, Git understands where to push future commits when only this command is used:

```bash
git push
```

---

## 16. Daily Git Workflow

After changing project files, the standard workflow is:

```bash
git status
git add .
git commit -m "commit message"
git push
```

### Workflow Explanation

1. `git status` shows the current changes.
2. `git add .` moves the changes to the Staging Area.
3. `git commit` saves a snapshot in Git History.
4. `git push` sends the local commits to GitHub.

Example:

```bash
git status
git add .
git commit -m "docs: add Python OOP notes"
git push
```

---

## 17. Complete Workflow Diagram

```text
Edit files
    ↓
Working Directory
    ↓ git status
Review changes
    ↓ git add .
Staging Area
    ↓ git commit
Local Git History
    ↓ git push
GitHub Remote Repository
```

---

## Commands Practiced

```bash
git init
git config --global user.name "maig"
git config --global user.email "your-email@example.com"
git config --global init.defaultBranch main
git config --list --show-origin
git branch -M main
git status
git add .
git add README.md
git commit -m "Initial learning notes"
git commit -m "Update README progress"
git log
git remote add origin git@github.com:imaige/ai-engineering-journey.git
git remote -v
ssh -T git@github.com
git push -u origin main
git push
```

---

## What I Understand Now

I can explain:

- what Git is
- the difference between Git and GitHub
- what a repository is
- what `.git` stores
- what a branch is
- the difference between `master` and `main`
- how global Git configuration works
- how a local repository is initialized
- the difference between the Working Directory, Staging Area, and Git History
- what `git status` shows
- what `git add` does
- what a commit is
- how commit messages should be written
- how `git log` displays project history
- what a remote repository is
- what `origin` means
- how SSH authentication connects Git to GitHub
- why GitHub SSH was configured through port `443`
- what `git push` does
- what the `-u` option does
- what an upstream branch is
- how the daily Git workflow works
- what a clean working tree means

---

## Key Takeaways

- Git tracks project changes locally.
- GitHub stores and shares repositories remotely.
- The Working Directory contains current project files.
- The Staging Area contains changes prepared for a commit.
- Git History contains committed snapshots.
- `git status` shows the repository's current state.
- `git add` prepares changes for a commit.
- `git commit` saves staged changes locally.
- `git log` displays commit history.
- `origin` is the conventional name of the main remote repository.
- SSH provides secure authentication with GitHub.
- `git push` sends local commits to GitHub.
- An upstream branch connects a local branch to its remote branch.
- A clean working tree means there are no uncommitted changes.

---

## Next Topics

These topics have not been studied yet and will be added after they are learned:

- `git diff`
- `.gitignore`
- `git pull`
- `git fetch`
- creating and switching branches
- merging branches
- resolving merge conflicts
- undoing changes safely
