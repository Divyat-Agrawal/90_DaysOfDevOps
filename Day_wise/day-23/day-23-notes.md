# 🚀 Day 23 – Git Branching & Working with GitHub

Until now, I learned:
- git init
- git add
- git commit
- git status

Today I learned the most powerful feature of Git:

🔥 **Branching**

---

# 🌳 Task 1 – Understanding Branches

## 1️⃣ What is a Branch in Git?

A branch in Git is a separate line of development.

It allows us to work on new features, bug fixes, or experiments without affecting the main code.

In simple words:

> A branch is like creating a copy of your project where you can safely work.

Each branch points to a specific commit.

---

## 2️⃣ Why do we use branches instead of committing everything to main?

We don’t commit everything to `main` because:

- We might break production code
- Multiple developers work on the same project
- Features may not be complete
- Bugs may exist
- Code may not be tested

Professional workflow:

1. Create a branch
2. Work on feature
3. Test
4. Merge into main

This keeps the project clean and safe.

---

## 3️⃣ What is HEAD in Git?

HEAD is a pointer.

It tells Git:

> "You are currently here."

It points to the current branch you are working on.

To check:

```bash
git branch
```

Example output:

```
* main
  feature-1
```

The `*` shows the current branch.

That means HEAD is pointing to `main`.

---

## 4️⃣ What happens to your files when you switch branches?

When you switch branches:

```bash
git switch feature-1
```

Git:
- Changes your working directory files
- Changes the project version
- Moves HEAD to the new branch

Your project becomes exactly how that branch was at its latest commit.

---

# 🛠 Task 2 – Branching Commands (Hands-On)

## 1️⃣ List all branches

```bash
git branch
```

Shows all local branches.

---

## 2️⃣ Create a new branch

```bash
git branch feature-1
```

Creates branch but does NOT switch to it.

---

## 3️⃣ Switch to feature-1

```bash
git switch feature-1
```

Now you are inside feature-1.

---

## 4️⃣ Create and switch in one command

Old way:

```bash
git checkout -b feature-2
```

Modern way:

```bash
git switch -c feature-2
```

`-c` means create.

This creates and switches to the branch.

---

## 5️⃣ Difference between git switch and git checkout

| git checkout | git switch |
|--------------|------------|
| Older command | Modern command |
| Used for multiple purposes | Only for switching branches |
| Can be confusing | More clear and safe |

Modern Git prefers `git switch`.

---

## 6️⃣ Make a commit in feature-1

Switch to branch:

```bash
git switch feature-1
```

Create file:

```bash
echo "This is feature 1" > feature1.txt
```

Add:

```bash
git add feature1.txt
```

Commit:

```bash
git commit -m "Added feature1 file"
```

This commit exists only in feature-1.

---

## 7️⃣ Switch back to main

```bash
git switch main
ls
```

You will NOT see `feature1.txt`.

Why?

Because that commit exists only in feature-1 branch.

That is the power of branching.

---

## 8️⃣ Delete a branch

Delete safely:

```bash
git branch -d feature-2
```

Force delete:

```bash
git branch -D feature-2
```

---

# 🌍 Task 3 – Push to GitHub

## 1️⃣ Create new repository on GitHub

- Go to GitHub
- Create new repository
- Do NOT initialize with README

---

## 2️⃣ Connect local repo to GitHub

```bash
git remote add origin https://github.com/username/devops-git-practice.git
```

Check remote:

```bash
git remote -v
```

`origin` means the remote repository.

---

## 3️⃣ Push main branch

```bash
git push -u origin main
```

Explanation:

- push → send code to GitHub
- -u → set upstream tracking
- origin → remote name
- main → branch name

After this, you can simply use:

```bash
git push
```

---

## 4️⃣ Push feature-1 branch

```bash
git push -u origin feature-1
```

Now both branches are visible on GitHub.

---

## 5️⃣ Difference between origin and upstream

| Term | Meaning |
|------|---------|
| origin | Your remote repository |
| upstream | Original repository (if you forked from someone) |

If you fork a repo:

- Your fork = origin
- Original repo = upstream

---

# 🔄 Task 4 – Fetch vs Pull

## git fetch

```bash
git fetch
```

- Downloads changes from remote
- Does NOT merge them

Think:
Download only.

---

## git pull

```bash
git pull
```

- Fetch + Merge
- Downloads and applies changes

Think:
Download and update immediately.

---

# 🍴 Task 5 – Clone vs Fork

## Clone

```bash
git clone https://github.com/user/repo.git
```

Creates a copy of repository on your local machine.

Clone is a Git command.

---

## Fork

Fork is done on GitHub website.

It creates a copy of repository in your GitHub account.

Fork is a GitHub concept, not a Git concept.

---

## Difference between Clone and Fork

| Clone | Fork |
|-------|------|
| Local copy | GitHub copy |
| Git command | GitHub feature |
| Used to download | Used to contribute |

---

## When to use Clone vs Fork?

Use Clone:
- When you just want to use or explore a project.

Use Fork:
- When you want to contribute to someone else's repository.

---

## Keep Fork in Sync with Original Repo

Add upstream:

```bash
git remote add upstream https://github.com/original/repo.git
```

Fetch changes:

```bash
git fetch upstream
```

Merge:

```bash
git merge upstream/main
```

Now your fork is updated.

---

# 🎯 What I Learned Today

- What is a branch
- Why we use branches
- What is HEAD
- How to create, switch, and delete branches
- How to push branches to GitHub
- Difference between origin and upstream
- Difference between fetch and pull
- Difference between clone and fork
- How to sync a fork

---

# 🔥 Conclusion

Branching makes Git powerful.

If you understand branching clearly,
you are no longer a beginner.

You are thinking like a real developer.

---

#90DaysOfDevOps  
#DevOpsKaJosh  
#TrainWithShubham
