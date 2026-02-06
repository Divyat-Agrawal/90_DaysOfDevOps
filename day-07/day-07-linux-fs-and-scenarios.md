# 🐧 Day 07 – Linux File System Hierarchy & Scenario Practice

This note covers two important areas:
1. Linux File System Hierarchy (where things live)
2. Scenario-based troubleshooting (how to think like a DevOps engineer)
---

# 📁 PART 1: Linux File System Hierarchy

## `/` — Root Directory
The starting point of the Linux file system. Everything exists under this.

```bash
ls -l /
```
I would use this when exploring the overall system structure.

---

## `/home` — User Directories
Each user has their own home directory here.

```bash
ls -l /home
```
Used when working with user files, scripts, and projects.

---

## `/root` — Root User’s Home
Home directory of the system administrator.

```bash
ls -l /root
```
Used when performing system-level administrative tasks.

---

## `/etc` — Configuration Files
Stores system and service configuration files.

```bash
ls -l /etc | head
cat /etc/hostname
```
Used when editing settings for services like SSH, nginx, cron, etc.

---

## `/var/log` — Log Files
Stores logs for the system and applications.

```bash
ls -l /var/log | head
du -sh /var/log/* 2>/dev/null | sort -h | tail -5
```
Used when troubleshooting service failures and system errors.

---

## `/tmp` — Temporary Files
Temporary storage used by the system and users.

```bash
ls -l /tmp
```
Used for short-term files and testing.

---

## `/bin` — Essential Commands
Core Linux command binaries live here.

```bash
ls -l /bin | head
```

---

## `/usr/bin` — Installed Programs
Most user-installed programs are stored here.

```bash
ls -l /usr/bin | head
```

---

## `/opt` — Optional Software
Used for third-party or custom-installed applications.

```bash
ls -l /opt
```

---

# 🧠 PART 2: Scenario-Based Troubleshooting

## 🔧 Scenario 1: Service Not Starting

A service called `myapp` failed to start after reboot.

### Step 1 — Check service status
```bash
systemctl status myapp
```
Shows if the service is running, stopped, or failed.

### Step 2 — Check service logs
```bash
journalctl -u myapp -n 50
```
Shows recent log messages explaining the failure.

### Step 3 — Check if service starts on boot
```bash
systemctl is-enabled myapp
```
Confirms if the service is enabled at startup.

### Step 4 — Confirm the service exists
```bash
systemctl list-units --type=service | grep myapp
```

---

## 🔥 Scenario 2: High CPU Usage

The server is slow.

### Step 1 — Check live CPU usage
```bash
top
```

### Step 2 — Find top CPU-consuming processes
```bash
ps aux --sort=-%cpu | head -10
```

### Step 3 — Stop the heavy process (carefully)
```bash
kill <PID>
```

---

## 📜 Scenario 3: Finding Service Logs

A developer asks where Docker logs are stored.

### Step 1 — Check Docker service status
```bash
systemctl status docker
```

### Step 2 — View last 50 log entries
```bash
journalctl -u docker -n 50
```

### Step 3 — Follow logs in real time
```bash
journalctl -u docker -f
```

---

## 🔒 Scenario 4: File Permission Issue

Script `/home/user/backup.sh` shows “Permission denied”.

### Step 1 — Check file permissions
```bash
ls -l /home/user/backup.sh
```

### Step 2 — Add execute permission
```bash
chmod +x /home/user/backup.sh
```

### Step 3 — Verify permissions
```bash
ls -l /home/user/backup.sh
```

### Step 4 — Run the script
```bash
./backup.sh
```

---

## ✅ What I Learned

- Where important Linux directories are located
- How to find logs and configuration files
- How to troubleshoot services and performance issues
- How to fix file permission problems
