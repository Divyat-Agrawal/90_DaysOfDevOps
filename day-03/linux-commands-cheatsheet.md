# 🐧 Linux Commands Cheat Sheet

A quick-reference guide for essential Linux commands used in file management, process monitoring, and networking troubleshooting.

---

## 📂 File System Commands

| Command | Description |
|---------|-------------|
| pwd | Show current directory |
| ls | List files and folders |
| ls -l | Detailed file list |
| cd folder | Change directory |
| cd .. | Move back one directory |
| mkdir folder | Create folder |
| touch file.txt | Create empty file |
| cp src dest | Copy file |
| mv old new | Move or rename file |
| rm file | Delete file |
| rm -r folder | Delete folder |
| cat file | View file contents |
| less file | Scroll through file |
| head file | First 10 lines |
| tail file | Last 10 lines |
| tail -f file | Monitor file live |

---

## ⚙️ Process Management

| Command | Description |
|---------|-------------|
| top | Live process monitor |
| htop | Advanced process monitor |
| ps aux | List all processes |
| ps aux \| grep name | Search process |
| kill PID | Stop process |
| kill -9 PID | Force stop process |
| jobs | List background jobs |
| bg | Resume in background |
| fg | Bring to foreground |
| uptime | System uptime/load |
| free -m | Memory usage |
| df -h | Disk usage |
| du -sh folder | Folder size |

---

## 🌐 Networking Commands

| Command | Description |
|---------|-------------|
| ip addr | Show IP address |
| ping host | Test connectivity |
| curl url | Fetch web response |
| wget url | Download file |
| ss -tulnp | Show open ports |
| netstat -tulnp | List listening services |
| dig domain | DNS lookup |
| nslookup domain | DNS lookup |
| traceroute host | Network path |

---

## 🧪 Example Troubleshooting

```bash
ps aux | grep nginx
top
ping google.com
curl http://localhost
