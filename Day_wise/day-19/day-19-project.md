# 🚀 Day 19 – Shell Scripting Project: Log Rotation, Backup & Crontab

Today I built real-world DevOps automation scripts using everything I learned in previous days.

This project includes:

- 🗂 Log Rotation Script
- 💾 Server Backup Script
- ⏰ Cron Scheduling
- 🛠 Combined Maintenance Script

These are real production-level tasks performed by DevOps engineers.

---

# 🔹 Task 1 – Log Rotation Script

## 🎯 Goal

- Take a log directory as argument
- Compress `.log` files older than 7 days
- Delete `.gz` files older than 30 days
- Print number of files processed
- Exit if directory does not exist

---

## 📝 `log_rotate.sh`

```bash
#!/bin/bash
set -euo pipefail

if [ "$#" -ne 1 ]; then
    echo "Usage: $0 <log_directory>"
    exit 1
fi

LOG_DIR="$1"

if [ ! -d "$LOG_DIR" ]; then
    echo "Error: Directory does not exist."
    exit 1
fi

echo "Starting log rotation in $LOG_DIR"

COMPRESS_COUNT=$(find "$LOG_DIR" -type f -name "*.log" -mtime +7 | wc -l)

find "$LOG_DIR" -type f -name "*.log" -mtime +7 -exec gzip {} \;

DELETE_COUNT=$(find "$LOG_DIR" -type f -name "*.gz" -mtime +30 | wc -l)

find "$LOG_DIR" -type f -name "*.gz" -mtime +30 -delete

echo "Compressed files: $COMPRESS_COUNT"
echo "Deleted old files: $DELETE_COUNT"
```

---

## 🧠 Explanation

- `-type f` → Select only files  
- `-name "*.log"` → Match log files  
- `-mtime +7` → Older than 7 days  
- `gzip` → Compress files  
- `-delete` → Remove old compressed files  

---

# 🔹 Task 2 – Server Backup Script

## 🎯 Goal

- Take source directory
- Take backup destination
- Create timestamped `.tar.gz` archive
- Verify backup
- Delete backups older than 14 days

---

## 📝 `backup.sh`

```bash
#!/bin/bash
set -euo pipefail

if [ "$#" -ne 2 ]; then
    echo "Usage: $0 <source_dir> <backup_dir>"
    exit 1
fi

SOURCE="$1"
DEST="$2"

if [ ! -d "$SOURCE" ]; then
    echo "Error: Source directory does not exist."
    exit 1
fi

mkdir -p "$DEST"

TIMESTAMP=$(date +%Y-%m-%d)
ARCHIVE_NAME="backup-$TIMESTAMP.tar.gz"

echo "Creating backup..."

tar -czf "$DEST/$ARCHIVE_NAME" "$SOURCE"

if [ -f "$DEST/$ARCHIVE_NAME" ]; then
    echo "Backup created successfully."
    ls -lh "$DEST/$ARCHIVE_NAME"
else
    echo "Backup failed!"
    exit 1
fi

find "$DEST" -type f -name "backup-*.tar.gz" -mtime +14 -delete
```

---

## 🧠 Explanation

- `mkdir -p` → Create directory if not exists  
- `date +%Y-%m-%d` → Generate timestamp  
- `tar -czf` → Create compressed archive  
- `-f` → Check if file exists  
- `-mtime +14` → Delete backups older than 14 days  

---

# 🔹 Task 3 – Crontab Scheduling

## 🧠 Cron Format

```
* * * * * command
| | | | |
| | | | └─ Day of week (0-7)
| | | └─── Month (1-12)
| | └───── Day of month (1-31)
| └─────── Hour (0-23)
└───────── Minute (0-59)
```

---

## 📌 Cron Entries

### Run log rotation daily at 2 AM

```
0 2 * * * /path/to/log_rotate.sh /var/log/myapp
```

---

### Run backup every Sunday at 3 AM

```
0 3 * * 0 /path/to/backup.sh /source /backup
```

---

### Run health check every 5 minutes

```
*/5 * * * * /path/to/health_check.sh
```

---

# 🔹 Task 4 – Maintenance Script (Combine Everything)

## 🎯 Goal

- Run log rotation
- Run backup
- Log output with timestamps

---

## 📝 `maintenance.sh`

```bash
#!/bin/bash
set -euo pipefail

LOG_FILE="/var/log/maintenance.log"

log_message() {
    echo "$(date): $1" >> "$LOG_FILE"
}

run_log_rotation() {
    log_message "Starting log rotation"
    /path/to/log_rotate.sh /var/log/myapp
    log_message "Log rotation completed"
}

run_backup() {
    log_message "Starting backup"
    /path/to/backup.sh /source /backup
    log_message "Backup completed"
}

main() {
    run_log_rotation
    run_backup
    log_message "Maintenance completed successfully"
}

main
```

---

## 📌 Cron Entry for Maintenance Script

Run daily at 1 AM:

```
0 1 * * * /path/to/maintenance.sh
```

---

# 📁 Folder Structure

```
2026/day-19/
│
├── log_rotate.sh
├── backup.sh
├── maintenance.sh
└── day-19-project.md
```

---

# 🧠 What I Learned

1. How to manage logs safely using `find`
2. How to create compressed backups using `tar`
3. How to automate tasks using cron
4. How to log script execution with timestamps
5. How to combine multiple scripts into one automation workflow



