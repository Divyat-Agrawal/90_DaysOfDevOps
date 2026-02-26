# 🚀 Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry Pick

Today I learned how branches come back together and how to handle advanced Git situations like a real developer.

This includes:

- Merge
- Rebase
- Squash
- Stash
- Cherry Pick

Everything explained in simple language.

---

# 🌿 Task 1 – Git Merge (How Branches Join Together)

## 🧠 What is Merge?

Merge means:

> Combining changes from one branch into another branch.

When we finish working on a feature branch, we merge it into `main`.

---

## ✅ Step 1: Create feature-login branch

```bash
git switch main
git switch -c feature-login
```

Explanation:
- `git switch main` → Move to main branch
- `-c feature-login` → Create new branch from current position

Add commits:

```bash
echo "Login Page" > login.txt
git add login.txt
git commit -m "Added login page"

echo "Login validation" >> login.txt
git add login.txt
git commit -m "Added login validation"
```

---

## ✅ Step 2: Merge into main

```bash
git switch main
git merge feature-login
```

### 🔎 What happened?

If no new commit was added to main after creating the branch, Git performs:

## ⚡ Fast-Forward Merge

### What is Fast-Forward Merge?

Main simply moves forward to match feature branch.

Before:

```
A --- B (main)
        \
         C --- D (feature-login)
```

After:

```
A --- B --- C --- D (main)
```

No merge commit created.

---

## 🔁 Creating a Merge Commit

### Create feature-signup

```bash
git switch -c feature-signup
```

Add commit:

```bash
echo "Signup Page" > signup.txt
git add signup.txt
git commit -m "Added signup page"
```

### Add commit to main

```bash
git switch main
echo "Hotfix" > hotfix.txt
git add hotfix.txt
git commit -m "Hotfix commit"
```

### Merge feature-signup

```bash
git merge feature-signup
```

Now Git creates a:

## 🔀 Merge Commit

Because both branches moved forward.

---

## ❗ What is a Merge Conflict?

A merge conflict happens when:

Both branches modify the same line of the same file.

Example:

On main:
```
Hello World
```

On feature:
```
Hello DevOps
```

Git shows:

```
<<<<<<< HEAD
Hello World
=======
Hello DevOps
>>>>>>> feature-branch
```

You must manually fix it.

Then:

```bash
git add file.txt
git commit
```

Conflict resolved.

---

# 🌊 Task 2 – Git Rebase (Clean History Method)

## 🧠 What is Rebase?

Rebase means:

> Move your branch on top of another branch.

Instead of combining histories like merge, rebase rewrites history to make it straight.

---

## ✅ Create feature-dashboard

```bash
git switch main
git switch -c feature-dashboard
```

Add commits:

```bash
echo "Dashboard UI" > dashboard.txt
git add dashboard.txt
git commit -m "Added dashboard UI"

echo "Dashboard API" >> dashboard.txt
git add dashboard.txt
git commit -m "Added dashboard API"
```

---

## ✅ Move main forward

```bash
git switch main
echo "Security patch" > security.txt
git add security.txt
git commit -m "Security patch"
```

---

## ✅ Rebase feature-dashboard

```bash
git switch feature-dashboard
git rebase main
```

### 🔎 What does rebase do?

Before:

```
A --- B --- E (main)
       \
        C --- D (feature-dashboard)
```

After:

```
A --- B --- E --- C' --- D'
```

It replays your commits on top of main.

---

## ❗ Why NEVER rebase pushed commits?

Because rebase rewrites history.

If someone already pulled those commits, their history will break.

Golden Rule:

> Never rebase shared commits.

---

## 🆚 Rebase vs Merge

Use Merge:
- In team projects
- For shared branches

Use Rebase:
- For personal branches
- For clean history before pushing

---

# 🧹 Task 3 – Squash Commit vs Regular Merge

## ✅ Create feature-profile

```bash
git switch -c feature-profile
```

Make small commits:

```bash
git commit -m "Added profile page"
git commit -m "Fixed typo"
git commit -m "Formatting fix"
git commit -m "Minor improvement"
```

---

## ✅ Squash merge

```bash
git switch main
git merge --squash feature-profile
git commit -m "Added profile feature"
```

### 🔎 What happened?

Instead of multiple commits, main gets only 1 commit.

---

## 📌 What is Squash Merge?

It combines all commits into one single commit.

---

## 🔁 Regular Merge

```bash
git merge feature-settings
```

Regular merge keeps all commits separately.

---

## 🎯 When to use squash?

Use squash when:
- Many small messy commits
- Want clean main branch

Trade-off:
- You lose detailed commit history

---

# 📦 Task 4 – Git Stash (Temporary Save)

## 🧠 What is Stash?

Stash means:

> Temporarily save unfinished work without committing.

---

## ✅ Make uncommitted changes

```bash
echo "Work in progress" >> login.txt
```

Try switching:

```bash
git switch main
```

Git may stop you.

---

## ✅ Save using stash

```bash
git stash
```

Now changes are saved safely.

---

## ✅ Bring changes back

```bash
git stash pop
```

---

## 🆚 Difference: pop vs apply

| pop | apply |
|-----|-------|
| Applies and removes stash | Applies but keeps stash |

---

## 📌 When to use stash?

- Urgent bug fix
- Switching tasks temporarily
- Not ready to commit

---

# 🍒 Task 5 – Cherry Pick

## 🧠 What is Cherry Pick?

Cherry pick means:

> Copy one specific commit from another branch.

---

## ✅ Create feature-hotfix

```bash
git switch -c feature-hotfix
```

Make 3 commits.

Check commit hashes:

```bash
git log --oneline
```

Example:

```
a1b2c3 Fix typo
d4e5f6 Security fix
g7h8i9 UI update
```

---

## ✅ Cherry pick second commit

```bash
git switch main
git cherry-pick d4e5f6
```

Now only that commit is added to main.

---

## 📌 When to use cherry-pick?

- Urgent production fix
- Apply one bug fix to another branch
- Hotfix scenario

---

## ⚠ What can go wrong?

- Duplicate commits
- Merge conflicts
- Messy history

---

# 🏆 What I Learned Today

- Fast-forward merge
- Merge commit
- Merge conflict
- Rebase and history rewriting
- Squash merge
- Stash usage
- Cherry-pick

#90DaysOfDevOps  
#DevOpsKaJosh  
#TrainWithShubham
