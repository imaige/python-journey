# Git Fundamentals

## Overview

This document summarizes the Git fundamentals I learned while setting up my `python-journey` repository.

## 1. What is Git?

Git is a version control system.

It tracks changes made to a project and allows developers to:

- keep a history of their work
- return to an earlier version
- work safely on new features
- collaborate with other developers

Git works locally on a computer.

GitHub is an online platform used to store and share Git repositories.

---

## 2. Repository

A repository, or repo, is a project that Git tracks.

Example:

```text
python-journey/
```

A normal folder becomes a Git repository after running:

```bash
git init
```

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

Deleting `.git` does not delete the project files, but it removes the Git history and turns the folder back into a normal folder.

---

## 4. Commit

A commit is a saved snapshot of the project at a specific moment.

Example:

```bash
git commit -m "Add first Python lesson"
```

A commit helps developers:

- track progress
- understand what changed
- return to an earlier version
- organize project history

A good commit message should briefly explain the change.

---

## 5. Branch

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

After the feature is completed and tested, it can be merged into `main`.

---

## 6. `master` and `main`

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

## 7. Git Configuration

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

## 8. Creating a Repository

One method is to create the folder first:

```bash
mkdir python-journey
cd python-journey
git init
```

Another method is:

```bash
git init python-journey
```

The second command creates the folder and initializes Git inside it.

The first approach makes each step easier to understand:

- `mkdir` creates the folder
- `cd` enters the folder
- `git init` creates the Git repository

---

## 9. Git and GitHub Connection

SSH authentication was configured so the computer can communicate securely with GitHub.

Because port 22 was unavailable, GitHub SSH was configured to use port 443.

Example SSH configuration:

```text
Host github.com
    HostName ssh.github.com
    User git
    Port 443
    IdentityFile ~/.ssh/id_ed25519
```

The connection was successfully tested with:

```bash
ssh -T git@github.com
```

---

## What I Understand Now

I can explain:

- what Git is
- the difference between Git and GitHub
- what a repository is
- what `.git` stores
- what a commit is
- what a branch is
- why `main` is used
- how global Git configuration works
- how a local repository is initialized
- how SSH authentication connects Git to GitHub

## Next Topics

- `git status`
- staging area
- `git add`
- `git commit`
- remote repositories
- `origin`
- `git push`
- `git pull`
- `git fetch`
- merging branches
