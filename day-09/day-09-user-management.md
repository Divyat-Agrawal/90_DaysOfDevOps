# 🐧 Day 09 Challenge — Linux User & Group Management

This challenge focused on creating users, managing groups, and setting up shared directories for team collaboration.

---

## 👤 Users & Groups Created

**Users:**
- tokyo
- berlin
- professor
- nairobi

**Groups:**
- developers
- admins
- project-team

---

## 🔗 Group Assignments

| User      | Groups Belonging To |
|-----------|---------------------|
| tokyo     | developers, project-team |
| berlin    | developers, admins |
| professor | admins |
| nairobi   | project-team |

---

## 📁 PART 4 — Shared Developer Directory

### Goal
Allow members of the **developers** group to collaborate in a shared project folder.

### Step 1 — Create Directory
```bash
sudo mkdir -p /opt/dev-project
```

### Step 2 — Check Current Ownership
```bash
ls -ld /opt/dev-project
```

### Step 3 — Change Group Ownership
```bash
sudo chgrp developers /opt/dev-project
```

### Step 4 — Set Permissions
```bash
sudo chmod 775 /opt/dev-project
```

Permission meaning:
- Owner → Read, Write, Execute
- Group → Read, Write, Execute
- Others → Read, Execute

### Step 5 — Test Access
```bash
sudo -u tokyo touch /opt/dev-project/tokyo-file.txt
sudo -u berlin touch /opt/dev-project/berlin-file.txt
```

---

## 🧑‍🤝‍🧑 PART 5 — Team Workspace

### Goal
Create a workspace for the **project-team** group.

### Step 1 — Create User Nairobi
```bash
sudo useradd -m nairobi
sudo passwd nairobi
```

### Step 2 — Create Group
```bash
sudo groupadd project-team
```

### Step 3 — Add Users to Group
```bash
sudo usermod -aG project-team nairobi
sudo usermod -aG project-team tokyo
```

### Step 4 — Create Workspace Directory
```bash
sudo mkdir -p /opt/team-workspace
```

### Step 5 — Set Group Ownership
```bash
sudo chgrp project-team /opt/team-workspace
```

### Step 6 — Set Permissions
```bash
sudo chmod 775 /opt/team-workspace
```

### Step 7 — Test Access
```bash
sudo -u nairobi touch /opt/team-workspace/nairobi-file.txt
```

---

## 💻 Commands Used

```bash
sudo useradd -m tokyo
sudo useradd -m berlin
sudo useradd -m professor
sudo useradd -m nairobi

sudo passwd tokyo
sudo passwd berlin
sudo passwd professor
sudo passwd nairobi

sudo groupadd developers
sudo groupadd admins
sudo groupadd project-team

sudo usermod -aG developers tokyo
sudo usermod -aG developers,admins berlin
sudo usermod -aG admins professor
sudo usermod -aG project-team nairobi
sudo usermod -aG project-team tokyo

sudo mkdir -p /opt/dev-project
sudo chgrp developers /opt/dev-project
sudo chmod 775 /opt/dev-project

sudo mkdir -p /opt/team-workspace
sudo chgrp project-team /opt/team-workspace
sudo chmod 775 /opt/team-workspace
```

---

## 🧠 What I Learned

1. How Linux users and groups control access  
2. How shared directories allow team collaboration  
3. How permissions (chmod) and group ownership (chgrp) work together  
4. How DevOps teams manage server access safely
