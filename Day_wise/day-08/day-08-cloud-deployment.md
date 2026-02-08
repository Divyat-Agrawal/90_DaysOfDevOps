
# 🚀 Day 08 – Deploying My First Real Cloud Server (Docker, Nginx & Logs)

Today was a major milestone in my DevOps journey. Instead of working only on my local machine, I deployed a **real server on the cloud**, connected to it remotely, installed a web server, and made my webpage accessible from the internet.

This is exactly how real-world production servers are deployed and managed.

In this blog, I’ll explain **each step**, **each command**, and **what is happening behind the scenes** in simple words so that even a beginner can understand.

---

## 🌍 What We Built Today

We created this flow:

**Cloud Server → Nginx Web Server → Internet → Browser**

When someone types our server’s IP address in a browser, the request travels over the internet to our cloud server. The Nginx web server then responds with a webpage.

---

# ☁️ PART 1 – Launching the Cloud Server

We used AWS EC2 to rent a virtual computer in the cloud.

Think of EC2 like this:  
> “Give me a computer in your data center that I can control from my laptop.”

---

## 🖥️ Step 1: Creating the EC2 Instance

Inside AWS:

1. Opened the **EC2 Dashboard**
2. Clicked **Launch Instance**
3. Selected **Ubuntu** as the Operating System
4. Chose **t2.micro (Free Tier eligible)**
5. Created a **Key Pair (.pem file)**
6. Configured Security Group to allow:
   - SSH (Port 22)
   - HTTP (Port 80)

After launching, AWS provided a **Public IP Address**.  
This is the internet address of our cloud server.

---

## 🔐 Step 2: Connecting to the Server Using SSH

Before connecting, we secured our key file:

```bash
chmod 400 my-key.pem
````

### Why is this needed?

SSH refuses to use a key file if other users have permission to access it.
This command ensures that only the owner can read the file.

---

### SSH Login Command

```bash
ssh -i my-key.pem ubuntu@YOUR_PUBLIC_IP
```

| Part           | Meaning                            |
| -------------- | ---------------------------------- |
| ssh            | Secure remote login tool           |
| -i my-key.pem  | Use this private key               |
| ubuntu         | Default username for Ubuntu server |
| YOUR_PUBLIC_IP | Address of our cloud server        |

After running this command, the terminal started controlling the remote cloud machine.

---

# 🛠️ PART 2 – Preparing the Server

A new server is like a brand-new computer. We must update it and install necessary software.

---

## 🔄 Step 1: Updating the System

```bash
sudo apt update && sudo apt upgrade -y
```

| Command     | Meaning                            |
| ----------- | ---------------------------------- |
| sudo        | Run as administrator               |
| apt update  | Refresh list of available software |
| apt upgrade | Install latest updates             |
| -y          | Automatically confirm              |

This keeps the server secure and up to date.

---

## 🐳 Step 2: Installing Docker

Docker allows us to run applications inside containers.

```bash
sudo apt install docker.io -y
```

Start Docker:

```bash
sudo systemctl start docker
```

Enable Docker at startup:

```bash
sudo systemctl enable docker
```

Check installation:

```bash
docker --version
```

---

## 🌐 Step 3: Installing Nginx Web Server

Nginx is software that serves web pages to users.

```bash
sudo apt install nginx -y
```

Start Nginx:

```bash
sudo systemctl start nginx
```

Enable it on boot:

```bash
sudo systemctl enable nginx
```

Check status:

```bash
sudo systemctl status nginx
```

If it shows **active (running)**, the web server is working correctly.

---

# 🔥 PART 3 – Making the Website Accessible from the Internet

Even though Nginx is running, the outside world cannot reach it yet. AWS uses a firewall called a **Security Group**.

We must allow web traffic.

---

## 🚪 Opening Port 80

In the AWS Security Group settings, we added this rule:

| Type | Port | Source               |
| ---- | ---- | -------------------- |
| HTTP | 80   | Anywhere (0.0.0.0/0) |

This tells AWS:

> “Allow anyone on the internet to access this server’s website.”

---

## 🌍 Testing in Browser

Opened a browser and visited:

```
http://YOUR_PUBLIC_IP
```

The **Nginx Welcome Page** appeared 🎉
This confirmed that my cloud server is now serving a live webpage on the internet.

---

# 📊 PART 4 – Working with Nginx Logs

Logs are like CCTV cameras for servers. They record visitor activity and errors.

---

## 📂 Navigating to Nginx Logs

```bash
cd /var/log/nginx
ls
```

| File       | Purpose                  |
| ---------- | ------------------------ |
| access.log | Records visitor requests |
| error.log  | Records server problems  |

---

## 👀 Viewing Logs

```bash
cat access.log
```

This shows:

* Visitor IP address
* Date and time
* Request type
* Status code

---

## 💾 Saving Logs to a File

```bash
cp access.log ~/nginx-logs.txt
```

This copies the log file into the home directory with a new name.

---

## ⬇️ Downloading Log File to Local Machine

After exiting the server:

```bash
exit
```

Run this on your local machine:

```bash
scp -i my-key.pem ubuntu@YOUR_PUBLIC_IP:~/nginx-logs.txt .
```

This transfers the log file from the cloud server to your computer.

---

# 📝 Documentation Summary

## Commands Used

* `chmod 400 key.pem`
* `ssh -i key.pem ubuntu@ip`
* `sudo apt update && sudo apt upgrade -y`
* `sudo apt install docker.io nginx -y`
* `sudo systemctl start nginx`
* `sudo systemctl enable nginx`
* `cat /var/log/nginx/access.log`
* `scp ubuntu@ip:~/nginx-logs.txt .`

---

## Challenges Faced

**SSH Permission Denied**
Solved by setting correct permissions using `chmod 400`.

**Nginx Page Not Loading**
Fixed by allowing HTTP (Port 80) in AWS Security Group.

---

## What I Learned

* How cloud servers are launched
* How SSH provides secure remote access
* How web servers deliver pages over the internet
* Importance of firewall and port rules
* How logs help monitor and troubleshoot servers

---

# 🎯 Why This Task Matters

This task gave me real-world DevOps experience:

✔ Cloud infrastructure provisioning
✔ Remote server management
✔ Web server deployment
✔ Log monitoring
✔ Network security basics
