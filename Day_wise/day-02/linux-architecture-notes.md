# Linux Architecture, Processes, and systemd

## Linux Architecture

Linux works in layers:

Hardware → Kernel → Shell → Applications

### Hardware
Physical components like CPU, RAM, and Disk.

### Kernel
The core of Linux. It manages CPU, memory, devices, and processes.

### Shell
Interface where users type commands (bash terminal).

### Applications
Programs like Nginx, MySQL, Docker, etc.

---

## How They Work Together

When a user runs a command:

User → Shell → Kernel → Hardware → Output back to user

The kernel performs the actual work by communicating with hardware.

---

## What is a Process?

A process is a running program.

Example:
Starting Nginx creates a process.

Commands to see processes:

ps aux  
top  

Each process has a PID, memory usage, CPU usage, and a state.

---

## Process States

Running   – Currently using CPU  
Sleeping  – Waiting for something (very common)  
Stopped   – Paused manually  
Zombie    – Finished but not cleaned up  

---

## What is systemd?

systemd is the service manager of Linux. It starts and manages system services.

Examples of services:
SSH, Nginx, Docker, Database servers

---

## Useful systemd Commands

systemctl start nginx  
systemctl stop nginx  
systemctl restart nginx  
systemctl status nginx  
systemctl enable nginx  
systemctl disable nginx  
journalctl -u nginx  

---

## 5 Daily Linux Commands

ps aux  
top  
htop  
kill <PID>  
systemctl status <service>  

---

Understanding Linux architecture, processes, and systemd is essential for troubleshooting in DevOps environments.
