# 🌐 Day 14 – Networking Fundamentals & Real Troubleshooting (Deep Dive)

Today I stepped into one of the most important areas of DevOps: **networking**.

Whenever a website doesn’t open, a server becomes unreachable, or an API stops responding, the issue is often not the application — it’s the **network path between systems**.

So today I didn’t just read theory. I learned how networking works in layers and practiced the **exact commands engineers use in real production incidents**.

---

## 🧠 Part 1 – Understanding Networking Models (Without Complicated Theory)

When data travels from my laptop to a website, it doesn’t just “go.”  
It passes through layers, where each layer has a job.

Think of it like sending a courier package:

- One team packs it  
- Another labels it  
- Another decides the route  
- Another transports it  

---

### 🔹 The OSI Model (7 Layers – Detailed View)

| Layer | Role | Simple Meaning |
|------|------|----------------|
| 7. Application | User services | HTTP, DNS, FTP |
| 6. Presentation | Formatting | Encryption, compression |
| 5. Session | Managing sessions | Keeps connection alive |
| 4. Transport | End-to-end delivery | TCP, UDP, Ports |
| 3. Network | Logical addressing | IP address, routing |
| 2. Data Link | Local delivery | MAC address, switches |
| 1. Physical | Hardware | Cables, Wi-Fi signals |

---

### 🔹 TCP/IP Model (Real Internet Model)

| TCP/IP Layer | OSI Equivalent | Example |
|--------------|----------------|---------|
| Application | OSI 5–7 | HTTP, HTTPS, DNS |
| Transport | OSI 4 | TCP, UDP |
| Internet | OSI 3 | IP |
| Link | OSI 1–2 | Ethernet, Wi-Fi |

---

### 🔹 Real-Life Example

```bash
curl https://example.com
````

What happens behind the scenes:

1. **Application Layer** → HTTP request is created
2. **Transport Layer** → Sent using TCP port 443
3. **Internet Layer** → Packet routed using IP
4. **Link Layer** → Sent through Wi-Fi or Ethernet

---

# 🛠️ Part 2 – Hands-On Networking Commands

I used **google.com** as the target to run all checks.

---

## 🖥️ 1. Identify My Machine’s IP Address

```bash
hostname -I
```

or

```bash
ip addr show
```

Shows the IP address assigned to my system.
If no IP appears, the network interface may be down.

---

## 📡 2. Check Reachability Using ping

```bash
ping google.com
```

* Checks if the target is reachable
* Shows latency and packet loss

Healthy network = low latency + 0% packet loss.

---

## 🛣️ 3. Check the Route Using traceroute

```bash
traceroute google.com
```

Shows each router (hop) between my system and the destination.
Useful for identifying where delays or failures happen.

---

## 🔌 4. See Which Services Are Listening

```bash
ss -tulpn
```

Displays open ports and services running on the machine.

Example:

```
LISTEN 0 128 0.0.0.0:22
```

Means SSH is running on port 22.

---

## 🌍 5. Check DNS Resolution

```bash
dig google.com
```

or

```bash
nslookup google.com
```

Resolves domain name → IP address.
If this fails, DNS is the problem.

---

## 🌐 6. Check Web Server Response

```bash
curl -I https://google.com
```

Fetches HTTP headers only.

Example response:

```
HTTP/2 200
```

Means the web server is healthy.

---

## 🔄 7. View Active Connections

```bash
netstat -an | head
```

Shows active and listening connections.

States include:

* LISTEN
* ESTABLISHED

---

# 🎯 Mini Task – Port Testing

Identify a listening port:

```bash
ss -tulpn | grep LISTEN
```

Test it locally:

```bash
nc -zv localhost 22
```

If connection succeeds → Port reachable
If not → Check service status or firewall

---

# 💭 Reflection

**Fastest command to detect problems:**
`ping`

**If DNS fails:**
Check DNS server (Application layer)

**If HTTP 500 error appears:**
Problem at Application layer (server-side issue)

**Two follow-up checks in real incidents:**

* Verify firewall rules
* Check application/service logs

---

# 🚀 Final Thoughts

Today I moved from just knowing networking terms to actually **testing and troubleshooting real network issues**.

Now I can confidently check:

✔ Is the host reachable?
✔ Where does the path fail?
✔ Is DNS resolving?
✔ Is the port open?
✔ Is the service responding?

That’s real DevOps troubleshooting.

---
