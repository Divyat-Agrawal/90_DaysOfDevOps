# 🐧 Day 12 – Breather & Deep Revision (Days 01–11)

For the last 11 days, I’ve been learning Linux and DevOps fundamentals daily.  
Today I didn’t rush into new topics. Instead, I slowed down and asked:

> “Do I really remember what I learned… or did I just complete tasks?”

Because in DevOps, you don’t get time to Google everything during an incident.  
You need **clarity + muscle memory** with commands.

So Day 12 was my **foundation strengthening day**.

---

## 🧠 1️⃣ Mindset & Learning Plan Check

**Purpose of this task:**  
Make sure I’m not just following a challenge blindly, but actually learning with direction.

On Day 01, my goal was:  
✔ Become comfortable with Linux  
✔ Understand how real servers work  
✔ Build discipline by learning daily  

### After 11 Days, Here’s What Changed

| Before | Now |
|-------|-----|
| Terminal felt scary | Terminal feels like a normal workspace |
| Commands felt random | Commands now feel connected |
| Linux was theory | Linux now feels practical |

### My Updated Focus Going Forward

- Practice commands **faster without thinking too much**
- Improve **troubleshooting mindset**
- Get better at understanding **logs and services**

---

## ⚙️ 2️⃣ Processes & Services – Real DevOps Skills

**Purpose of this task:**  
Practice checking what’s running in the system and whether services are healthy.

Because in real jobs, the first question is always:  
**“Why is the application not working?”**

---

### 🔹 Command: `ps aux`

```bash
ps aux | head
```

#### What this command shows:

- A full list of running processes  
- Which user started them  
- CPU and memory usage  

| Part | Meaning |
|------|---------|
| ps | Process status |
| a | All users’ processes |
| u | User-oriented format |
| x | Background processes |
| \| head | Show only top lines |

👉 This command helps me quickly check **if a process is running or consuming too much memory**.

---

### 🔹 Command: `systemctl status ssh`

```bash
systemctl status ssh
```

#### Why this matters:

Services are background programs like:
- ssh (remote login)
- nginx (web server)
- mysql (database)

This command tells me:  
✔ Service is active or not  
✔ Since when it has been running  
✔ If there are recent errors  

---

### 🔹 Command: `journalctl -u ssh`

```bash
journalctl -u ssh
```

This shows **logs of the SSH service**.

Logs are like a **diary of the system**.  
If something fails, logs tell *why*.

Example use in real life:  
> “Users can’t log in via SSH” → Check logs with `journalctl`

---

## 📁 3️⃣ File Skills – Strengthening the Basics

**Purpose of this task:**  
Make sure file operations feel natural.

---

### 🔹 Add text without deleting old content

```bash
echo "Revision in progress" >> notes.txt
```

`>>` means **append**, not overwrite.

---

### 🔹 Check file permissions and ownership

```bash
ls -l notes.txt
```

This shows:
- Who owns the file  
- Which group it belongs to  
- Who can read/write/execute  

---

### 🔹 Change permissions safely

```bash
chmod 644 notes.txt
```

Meaning:
- Owner can read & write  
- Group can read  
- Others can read  

I now understand numbers like **644** instead of just memorizing them.

---

### 🔹 Change file owner

```bash
sudo chown tokyo notes.txt
```

This transfers ownership to another user — something needed in deployments.

---

### 🔹 Create directory for practice

```bash
mkdir revision-practice
```

Even small commands like this now feel automatic.

---

## 📚 4️⃣ My Personal Linux First-Aid Cheat Sheet

If a server breaks, these are the first commands I’d run:

| Command | Why I’d Use It |
|---------|----------------|
| `ls -l` | Check permissions & ownership |
| `cat file.log` | Read logs quickly |
| `ps aux` | Check running processes |
| `top` | See live CPU/memory usage |
| `systemctl status service` | Check if a service is down |

These commands are now becoming part of my **instinct**.

---

## 👥 5️⃣ User & Ownership Sanity Practice

**Purpose of this task:**  
Reinforce user and file ownership — important in real servers.

---

### 🔹 Create a user

```bash
sudo useradd revisionuser
```

---

### 🔹 Create a file

```bash
touch testfile.txt
```

---

### 🔹 Change ownership

```bash
sudo chown revisionuser testfile.txt
```

---

### 🔹 Check user details

```bash
id revisionuser
```

Shows:
- User ID  
- Group ID  
- Groups the user belongs to  

---

### 🔹 Verify file ownership

```bash
ls -l testfile.txt
```

Confirms that the ownership actually changed.

---

## ✅ Mini Self-Check (My Honest Answers)

### 1️⃣ Three commands that save me the most time

- `ls -l` → Instant file info  
- `ps aux` → Quick process overview  
- `systemctl status` → Immediate service health check  

---

### 2️⃣ How I check if a service is healthy

```bash
systemctl status nginx
journalctl -u nginx
ps aux | grep nginx
```

This checks:
✔ Status  
✔ Logs  
✔ Running process  

---

### 3️⃣ How to safely change ownership and permissions

```bash
sudo chown appuser:appgroup app.log
chmod 640 app.log
```

This avoids giving access to the wrong users.

---

### 4️⃣ What I’ll improve in next 3 days

- Speed with commands  
- Confidence reading logs  
- Practicing real troubleshooting scenarios  

---

## 🎯 Final Thoughts on Day 12

Today taught me something important:

> Learning DevOps is not about rushing forward —  
> it’s about building **strong basics** that don’t shake under pressure.

I feel more confident than Day 01.  
And I know that repeating these basics will make future topics easier.

---

