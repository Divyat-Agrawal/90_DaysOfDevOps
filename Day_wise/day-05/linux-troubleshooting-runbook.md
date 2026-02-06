# 🐧 Linux Troubleshooting Runbook — Day 05

This runbook captures a quick troubleshooting routine for checking CPU, memory, disk, network, and logs for a Linux service.

---

## 🎯 Target Service
SSH (Secure Shell) — Used for remote login to the server

---

## 🖥 Environment Basics

### Kernel Information
```bash
uname -a
```
Shows Linux kernel version and system architecture.

### Operating System Details
```bash
cat /etc/os-release
```
Displays Linux distribution name and version (Ubuntu, CentOS, etc.).

---

## ⚙️ Snapshot: CPU & Memory

### Live system resource usage
```bash
top
```
Shows real-time CPU and memory usage. Look for high CPU (>80%) or low free memory.

### Memory usage summary
```bash
free -h
```
Displays total and used RAM in human-readable format.

### SSH process resource usage
```bash
ps -o pid,pcpu,pmem,comm -p $(pgrep sshd)
```
Shows how much CPU and memory the SSH process is consuming.

---

## 💾 Snapshot: Disk & Storage

### Disk space usage
```bash
df -h
```
Shows disk usage for all mounted filesystems. Check for disks above 90% usage.

### Size of log directory
```bash
du -sh /var/log
```
Displays total size of logs. Large logs can fill disk and crash services.

---

## 🌐 Snapshot: Network

### Check if SSH is listening on port 22
```bash
ss -tulpn | grep ssh
```
Confirms SSH service is listening for connections.

### Test local web service response
```bash
curl -I http://localhost
```
Sends a request to check if a local web service responds with HTTP headers.

---

## 📜 Logs Reviewed

### Last 50 SSH service logs
```bash
journalctl -u ssh -n 50
```
Shows recent logs related to the SSH service.

### Last 50 system log lines
```bash
tail -n 50 /var/log/syslog
```
Displays latest system-wide events and warnings.

---

## 🔎 Quick Findings (Example)

- CPU usage normal  
- Memory usage stable  
- Disk space sufficient  
- SSH service active and listening  
- No critical errors in recent logs  

---

## 🚨 If This Worsens (Next Steps)

### Restart SSH service
```bash
sudo systemctl restart ssh
```
Restarts the SSH service safely.

### Watch SSH logs live
```bash
sudo journalctl -u ssh -f
```
Streams live SSH logs for real-time monitoring.

### Capture deeper diagnostics
```bash
strace -p <PID>
```
Traces system calls of a process if it hangs or behaves strangely.

---

## ✅ Conclusion

This runbook provides a repeatable checklist for troubleshooting Linux services quickly and confidently. It helps capture system health before taking action and reduces guesswork during incidents.
