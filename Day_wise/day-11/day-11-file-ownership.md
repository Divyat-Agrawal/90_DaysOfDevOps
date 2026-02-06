# 🐧 Day 11 – Understanding File Ownership in Linux (chown & chgrp)

Today I learned something that made me realize Linux is built for **multi-user systems**. Files are not just about read/write/execute permissions — they also belong to **specific users and groups**.

This is super important in DevOps because applications, logs, and deployments all depend on **correct ownership**.

Let’s break it down step by step.

---

## 📌 Task 1: Understanding File Ownership

**Goal of this task:**  
Before changing ownership, I first needed to understand how Linux currently assigns owners and groups to files.

I started by checking file ownership in my home directory:

```bash
ls -l
```

Sample output:

```
-rw-r--r-- 1 divyat divyat   0 Feb 6 10:00 devops.txt
-rw-r--r-- 1 divyat divyat  32 Feb 6 10:05 notes.txt
```

### Format Breakdown

```
-rw-r--r-- 1 owner group size date filename
```

| Column | Meaning |
|--------|---------|
| owner | The user who owns the file |
| group | The group that owns the file |

### 🤔 Owner vs Group

- **Owner** → The main user who controls the file  
- **Group** → A set of users who share access

Example:  
If a file belongs to user `divyat` and group `dev-team`, then:
- Only **divyat** is the owner  
- All users inside **dev-team group** get group permissions

---

## 🛠️ Task 2: Basic `chown` Operations (Change Owner)

**Goal of this task:**  
Learn how to transfer file ownership from one user to another.

### 1️⃣ Create a file

```bash
touch devops-file.txt
```

Check owner:

```bash
ls -l devops-file.txt
```

Output:

```
-rw-r--r-- 1 divyat divyat 0 devops-file.txt
```

Both owner and group are `divyat`.

---

### 2️⃣ Create new users (if not present)

```bash
sudo useradd tokyo
sudo useradd berlin
```

---

### 3️⃣ Change owner to **tokyo**

```bash
sudo chown tokyo devops-file.txt
```

Verify:

```bash
ls -l devops-file.txt
```

Now:

```
-rw-r--r-- 1 tokyo divyat 0 devops-file.txt
```

Owner changed ✅

---

### 4️⃣ Change owner to **berlin**

```bash
sudo chown berlin devops-file.txt
```

Now file owner becomes **berlin**.

---

## 👥 Task 3: Basic `chgrp` Operations (Change Group)

**Goal of this task:**  
Understand how to assign files to a specific team by changing their group ownership.

### 1️⃣ Create file

```bash
touch team-notes.txt
```

Check group:

```bash
ls -l team-notes.txt
```

---

### 2️⃣ Create group

```bash
sudo groupadd heist-team
```

---

### 3️⃣ Change file group

```bash
sudo chgrp heist-team team-notes.txt
```

Verify:

```bash
ls -l team-notes.txt
```

Now group changes from your default group to **heist-team**.

---

## 🔄 Task 4: Change Owner AND Group Together

**Goal of this task:**  
Learn how to assign both a new user and a new group in a single command.

### 1️⃣ Create file

```bash
touch project-config.yaml
```

### 2️⃣ Change owner to **professor** and group to **heist-team**

First create user:

```bash
sudo useradd professor
```

Then run:

```bash
sudo chown professor:heist-team project-config.yaml
```

Verify:

```bash
ls -l project-config.yaml
```

---

### 3️⃣ Change ownership of a directory

```bash
mkdir app-logs
sudo chown berlin:heist-team app-logs
```

Now the directory belongs to **berlin** and group **heist-team**.

---

## 🌳 Task 5: Recursive Ownership Change

**Goal of this task:**  
Apply ownership changes to an entire project folder and everything inside it.

### 1️⃣ Create directory structure

```bash
mkdir -p heist-project/vault
mkdir -p heist-project/plans
touch heist-project/vault/gold.txt
touch heist-project/plans/strategy.conf
```

---

### 2️⃣ Create group

```bash
sudo groupadd planners
```

---

### 3️⃣ Change ownership recursively

```bash
sudo chown -R professor:planners heist-project/
```

### What does `-R` mean?

`-R` = Recursive  
It changes ownership for:
- The folder  
- All subfolders  
- All files inside

---

### 4️⃣ Verify

```bash
ls -lR heist-project/
```

You’ll see **every file and folder** now belongs to `professor` and group `planners`.

---

## 🎯 Task 6: Practice Challenge

**Goal of this task:**  
Simulate a real DevOps environment where different team members and teams own different project files.

### 1️⃣ Create users

```bash
sudo useradd tokyo
sudo useradd berlin
sudo useradd nairobi
```

### 2️⃣ Create groups

```bash
sudo groupadd vault-team
sudo groupadd tech-team
```

---

### 3️⃣ Create directory and files

```bash
mkdir bank-heist
touch bank-heist/access-codes.txt
touch bank-heist/blueprints.pdf
touch bank-heist/escape-plan.txt
```

---

### 4️⃣ Assign ownership

```bash
sudo chown tokyo:vault-team bank-heist/access-codes.txt
sudo chown berlin:tech-team bank-heist/blueprints.pdf
sudo chown nairobi:vault-team bank-heist/escape-plan.txt
```

---

### 5️⃣ Verify

```bash
ls -l bank-heist/
```

Now each file has **different owner and group** — just like real production systems where different teams handle different resources.

---

## 🧠 What I Learned Today

1️⃣ Linux files belong to **users and groups**, not just permissions  
2️⃣ `chown` changes owner, `chgrp` changes group  
3️⃣ `chown owner:group` can change both at once  
4️⃣ `-R` is powerful — it updates entire directory trees  
5️⃣ Ownership is critical in DevOps for apps, logs, and deployments

---

## 🚀 Why This Matters in DevOps

In real environments:
- Web apps run as specific users  
- Logs must belong to logging services  
- Teams share folders using groups  
- Wrong ownership = **application crashes**

Learning this today made Linux feel more like a **real production system** rather than just a practice machine.

---


