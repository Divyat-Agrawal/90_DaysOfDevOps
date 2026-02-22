# 🚀 Day 22 – Introduction to Git: Your First Repository

Welcome to Day 22 of **#90DaysOfDevOps** 🎯

Today marks the beginning of your Git journey. Git is the backbone of modern DevOps — every tool, pipeline, and workflow revolves around version control.

Before moving to advanced Git concepts, we must deeply understand the basics.

---

# 📌 What You Will Learn

* What Git is and why it matters
* How to initialize your first repository
* How staging and commits work
* How Git internally stores history
* How to maintain a clean commit history

---

# 🧠 What is Git?

Git is a **Version Control System (VCS)**.

It helps you:

* Track changes in files
* Save versions of your project
* Collaborate safely
* Revert mistakes
* Maintain history of your work

Think of Git as:

> A time machine for your code.

---

# 🏗️ How Git Works Internally

Git works in **three main areas**:

1. **Working Directory**
2. **Staging Area**
3. **Repository**

Understanding these three areas is the key to mastering Git.

---

# ✅ Task 1 – Install and Configure Git

---

## 1️⃣ Verify Git Installation

```bash
git --version
```

### What this does:

* Displays installed Git version
* Confirms Git is installed

### Example:

```
git version 2.53.0.windows.1
```

---

## 2️⃣ Set Git Identity

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

### Explanation:

* `--global` sets configuration for all repositories
* Git attaches this info to every commit

---

## 3️⃣ Verify Configuration

```bash
git config --list
```

Shows:

* Username
* Email
* Git settings

---

# ✅ Task 2 – Create Your First Git Repository

---

## 1️⃣ Create Project Folder

```bash
mkdir devops-git-practice
cd devops-git-practice
```

* `mkdir` → Creates directory
* `cd` → Enters directory

---

## 2️⃣ Initialize Git

```bash
git init
```

Output:

```
Initialized empty Git repository
```

### What happens:

* Creates hidden `.git` folder
* Turns normal folder into Git repository

---

## 3️⃣ Check Repository Status

```bash
git status
```

Example:

```
On branch master
No commits yet
nothing to commit
```

### What `git status` shows:

* Current branch
* Staged files
* Modified files
* Untracked files

`git status` is your best friend in Git.

---

## 4️⃣ Explore `.git` Folder

```bash
ls -a
```

You will see:

```
.git
```

Inside `.git`:

```
HEAD
config
objects
refs
hooks
```

### What `.git` Contains:

* Commit history
* Branch information
* Configuration
* Git database

⚠️ If you delete `.git`, your project loses version control completely.

---

# ✅ Task 3 – Create Git Commands Reference

---

## Create File

```bash
touch git-commands.md
```

Check status:

```bash
git status
```

Output:

```
Untracked files:
  git-commands.md
```

### What "Untracked" Means:

Git sees the file but is not tracking it yet.

---

# ✅ Task 4 – Stage and Commit

---

## 1️⃣ Stage File

```bash
git add git-commands.md
```

### What this does:

* Moves file to staging area
* Prepares it for commit
* Takes a snapshot of current version

Think of it like:

> Selecting changes you want to save.

---

## 2️⃣ Check What’s Staged

```bash
git status
```

You’ll see:

```
Changes to be committed
```

---

## 3️⃣ Commit Changes

```bash
git commit -m "Add git-commands.md initial file"
```

### What commit does:

* Creates permanent snapshot
* Assigns unique commit ID
* Saves it in repository

Each commit contains:

* Commit ID (hash)
* Author
* Date
* Commit message

---

## 4️⃣ View Commit History

```bash
git log
```

Compact view:

```bash
git log --oneline
```

Example:

```
3d60d95 Add basic workflow commands
f01fed8 Add setup and version commands
9d7e6b7 Initial commit
```

---

# ✅ Task 5 – Make More Changes and Build History

Edit your file and then check changes:

```bash
git diff
```

### What `git diff` does:

* Shows line-by-line changes
* `+` means added
* `-` means removed

Stage and commit:

```bash
git add .
git commit -m "Add basic workflow commands"
```

Repeat at least 3 times to build a meaningful history.

---

# ✅ Task 6 – Understanding Git Workflow

---

## 🔹 Difference Between `git add` and `git commit`

* `git add` → Moves changes to staging area
* `git commit` → Saves staged changes permanently

---

## 🔹 What Does Staging Area Do?

It allows you to:

* Select specific changes
* Control what goes into commit

Without staging, Git would commit everything automatically.

---

## 🔹 What Does `git log` Show?

* Commit ID
* Author
* Date
* Commit message
* Commit history

---

## 🔹 What is `.git` Folder?

It is Git’s internal database.

It stores:

* All commits
* All branches
* All history
* All configuration

Deleting `.git` removes version control completely.

---

## 🔹 Working Directory vs Staging Area vs Repository

| Area              | Meaning                              |
| ----------------- | ------------------------------------ |
| Working Directory | Where you edit files                 |
| Staging Area      | Where you prepare changes            |
| Repository        | Where commits are permanently stored |

---

# 🎯 Final Git Workflow Summary

1. Edit file (Working Directory)
2. `git add` (Move to Staging Area)
3. `git commit` (Save in Repository)
4. `git log` (View history)

Repeat this cycle continuously.

---

# 🏆 What You Achieved Today

* Installed and configured Git
* Created your first repository
* Understood `.git` folder
* Created multiple commits
* Built clean commit history
* Understood Git architecture

This is the foundation of DevOps.

---
