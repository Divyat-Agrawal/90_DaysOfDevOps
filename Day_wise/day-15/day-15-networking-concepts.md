# 🌐 Day 15 – Understanding DNS, IP Addresses, Subnets & Ports (Beginner to DevOps Level)

Today I focused on the **foundations of networking** — the basic building blocks that power the entire internet.

Before today, terms like DNS, IP, CIDR, and Ports sounded technical.  
Now, I understand how they all connect when I open a website or when servers talk to each other.

Let’s break everything down in the simplest way possible.

---

# 🧭 PART 1 – DNS: How Names Become IP Addresses

## 🌍 What happens when you type `google.com` in a browser?

Computers don’t understand names like humans do. They understand numbers (IP addresses). So DNS acts like the **phonebook of the internet**.

Here’s what happens step-by-step:

1. Your browser asks: “What is the IP of google.com?”
2. Your system asks a DNS server.
3. DNS server replies with Google’s IP address.
4. Your browser connects to that IP and loads the website.

So DNS = **Name → Number translator**

---

## 📚 DNS Record Types (In One Line Each)

| Record | Meaning |
|--------|---------|
| **A** | Maps domain name → IPv4 address |
| **AAAA** | Maps domain name → IPv6 address |
| **CNAME** | One domain name points to another domain |
| **MX** | Mail server for a domain |
| **NS** | Nameservers responsible for a domain |

---

## 🛠 Command: `dig google.com`

```bash
dig google.com
````

### What this command does:

It asks a DNS server for information about google.com.

### Important parts of output:

* **ANSWER SECTION** → Shows IP address (A record)
* **TTL** → Time the DNS answer can be cached

Example:

```
google.com.   300   IN   A   142.250.183.14
```

Here:

* `A` record = 142.250.183.14
* TTL = 300 seconds

---

# 🧭 PART 2 – IP Addressing

## 🔢 What is an IPv4 Address?

An IPv4 address looks like this:

```
192.168.1.10
```

It has **4 numbers (octets)** separated by dots.
Each number ranges from 0–255.

Think of it like:
**Street.Building.Floor.Room**

It uniquely identifies a device on a network.

---

## 🌐 Public vs Private IP

| Type       | Meaning                      | Example      |
| ---------- | ---------------------------- | ------------ |
| Public IP  | Accessible from the internet | 8.8.8.8      |
| Private IP | Used inside local networks   | 192.168.1.10 |

Private IPs cannot be accessed directly from the internet.

---

## 🏠 Private IP Ranges

| Range                         | Used For                |
| ----------------------------- | ----------------------- |
| 10.0.0.0 – 10.255.255.255     | Large private networks  |
| 172.16.0.0 – 172.31.255.255   | Medium private networks |
| 192.168.0.0 – 192.168.255.255 | Home/office networks    |

---

## 🛠 Command: `ip addr show`

```bash
ip addr show
```

This shows all IP addresses on your system.

If you see something like:

```
inet 192.168.1.5/24
```

That is a **private IP**.

---

# 🧭 PART 3 – CIDR & Subnetting

## 📏 What does `/24` mean?

Example:

```
192.168.1.0/24
```

The `/24` means:
👉 First 24 bits are network part
👉 Last 8 bits are host part

That gives **256 total IP addresses**.

---

## 🧮 Hosts Calculation

| CIDR | Total IPs | Usable Hosts |
| ---- | --------- | ------------ |
| /24  | 256       | 254          |
| /16  | 65,536    | 65,534       |
| /28  | 16        | 14           |

Why minus 2?
One is for the **network address** and one is the **broadcast address**.

---

## 🧠 Why Do We Subnet?

Subnetting helps us:

* Organize networks
* Improve security
* Reduce network traffic
* Use IP addresses efficiently

Example: Separate subnets for:

* Servers
* Employees
* Guests

---

## 📋 CIDR Table

| CIDR | Subnet Mask     | Total IPs | Usable Hosts |
| ---- | --------------- | --------- | ------------ |
| /24  | 255.255.255.0   | 256       | 254          |
| /16  | 255.255.0.0     | 65,536    | 65,534       |
| /28  | 255.255.255.240 | 16        | 14           |

---

# 🧭 PART 4 – Ports: Doors to Services

## 🚪 What is a Port?

IP address = Building
Port = Room number

Ports allow multiple services to run on one machine.

---

## 📚 Common Ports

| Port  | Service            |
| ----- | ------------------ |
| 22    | SSH (Remote login) |
| 80    | HTTP (Web)         |
| 443   | HTTPS (Secure web) |
| 53    | DNS                |
| 3306  | MySQL Database     |
| 6379  | Redis              |
| 27017 | MongoDB            |

---

## 🛠 Command: `ss -tulpn`

```bash
ss -tulpn
```

This shows which ports are open and which services are using them.

Example:

```
LISTEN 0 128 0.0.0.0:22 users:(("sshd"))
```

Means SSH service is running.

---

# 🧭 PART 5 – Putting It All Together

## 🌐 When you run:

```bash
curl http://myapp.com:8080
```

Here’s what happens:

* DNS resolves `myapp.com` → IP address
* Connection is made to that IP on **port 8080**
* Uses HTTP protocol over TCP
* Server responds with web data

---

## 🛠 If an app can't reach DB at `10.0.1.50:3306`

I would check:

1. Is the IP reachable? (`ping`)
2. Is the port open? (`nc` or `ss`)
3. Is MySQL service running?
4. Are firewall rules blocking the connection?

---

# 🎓 What I Learned Today

* DNS converts domain names into IP addresses
* IP addresses uniquely identify devices on a network
* Subnets divide networks for better management and security
* Ports allow multiple services to run on one server

Networking now feels logical instead of confusing.


Whenever you're ready, we can make **Day 16** just as strong 🚀
```
