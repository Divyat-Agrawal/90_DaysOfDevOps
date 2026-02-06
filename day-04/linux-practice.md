# 🐧 Day 04 – Linux Practice: Processes, Services & Logs

This hands-on practice note captures essential Linux commands used to inspect running processes, check system services, and read logs for troubleshooting.

---

## ⚙️ Process Checks

### List running processes
```bash
ps aux | head
```
Shows currently running processes with CPU and memory usage.

### Alternate process view
```bash
ps -ef | head
```
Another format for viewing all processes.

### Live system monitor
```bash
top
```
Displays real-time CPU and memory usage. Press **q** to quit.

### Find process by name
```bash
pgrep sshd
```
Returns the Process ID (PID) of the SSH service.

### Get PID of a service
```bash
pidof nginx
```
Returns PID if nginx is running.

---

## 🛠 Service Checks

### Check SSH service status
```bash
systemctl status ssh
```
Shows whether the SSH service is active, inactive, or failed.

### Check nginx service status
```bash
systemctl status nginx
```
Verifies if the web server is running.

### List active services
```bash
systemctl list-units --type=service
```
Displays all active system services.

### Quick service health check
```bash
systemctl is-active docker
```
Returns `active` or `inactive`.

### Restart a service
```bash
sudo systemctl restart ssh
```
Restarts the SSH service during troubleshooting.

---

## 📜 Log Checks

### View logs for SSH service
```bash
journalctl -u ssh --since "10 minutes ago"
```
Shows recent logs related to SSH.

### View system errors
```bash
journalctl -xe
```
Displays recent system-level errors and warnings.

### View recent system logs
```bash
tail -n 50 /var/log/syslog
```
Shows the last 50 lines of system logs.

### Monitor nginx error logs live
```bash
tail -f /var/log/nginx/error.log
```
Displays live updates from nginx error logs.

### Check kernel messages
```bash
dmesg | tail
```
Shows recent kernel-level system messages.

---

## 🧪 Mini Troubleshooting Scenario — SSH Not Working

### Step 1 — Check if SSH process is running
```bash
pgrep sshd
```

### Step 2 — Check service health
```bash
systemctl status ssh
```

### Step 3 — Inspect logs
```bash
journalctl -u ssh --since "5 minutes ago"
```

### Step 4 — Restart service (if required)
```bash
sudo systemctl restart ssh
```

---

## ✅ Learning Outcome

By completing this practice, I learned how to:

- Inspect running processes  
- Monitor system resource usage  
- Check the status of system services  
- Read and analyze logs  
- Follow a basic Linux troubleshooting workflow  

These commands build strong fundamentals for real-world DevOps and Linux system administration.
