# 🐱 Hack The Box — Meow

![Hack The Box](https://img.shields.io/badge/Hack%20The%20Box-Meow-9FEF00?style=for-the-badge&logo=hackthebox&logoColor=black)
![Difficulty](https://img.shields.io/badge/Difficulty-Very%20Easy-success?style=for-the-badge)
![OS](https://img.shields.io/badge/OS-Linux-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Pwned-9FEF00?style=for-the-badge)

> Beginner Hack The Box machine focused on reconnaissance, service enumeration, Telnet, and initial access.

## 📋 Machine Information

| Field | Details |
|---|---|
| Platform | Hack The Box |
| Machine | Meow |
| Difficulty | Very Easy |
| OS | Linux |
| Primary Service | Telnet |
| Status | ✅ Pwned |

## ⛓️ Attack Chain

```text
Target
  ↓
Nmap Enumeration
  ↓
Port 23 / Telnet
  ↓
Service Enumeration
  ↓
Authentication
  ↓
Remote Shell
  ↓
Flag Discovery
```

## 1. 🔎 Reconnaissance

Verify connectivity to the HTB target:

```bash
ping -c 4 <TARGET_IP>
```

![Ping Test](screenshots/01-ping.png)

## 2. 🛰️ Nmap Enumeration

Run service and default-script detection:

```bash
nmap -sC -sV <TARGET_IP>
```

The scan identified an exposed Telnet service on port 23.

```text
PORT   STATE SERVICE
23/tcp open  telnet
```

![Nmap Scan](screenshots/02-nmap.png)

## 3. 🔐 Telnet Enumeration

Connect to the exposed Telnet service:

```bash
telnet <TARGET_IP> 23
```

![Telnet](screenshots/03-telnet.png)

## 4. 💻 Initial Access

After successful authentication using the credentials intended for the HTB lab, remote shell access was obtained.

Verify the current user:

```bash
whoami
```

Check system information:

```bash
uname -a
```

![Shell Access](screenshots/04-shell.png)

## 5. 🚩 Flag Discovery

Perform basic filesystem enumeration:

```bash
pwd
ls
```

The required flag was then located and displayed with:

```bash
cat <FLAG_FILE>
```

The actual flag is intentionally **not published** in this repository.

![Flag Discovery](screenshots/05-flag.png)

## 🧠 What I Learned

### Enumeration comes first

Before attempting exploitation, identify the services exposed by the target.

### Nmap is essential

The following command quickly revealed the available attack surface:

```bash
nmap -sC -sV <TARGET_IP>
```

### Telnet

Telnet is an older remote-access protocol and does not provide the secure encrypted communication associated with modern alternatives such as SSH.

### Methodology

```text
Recon
 ↓
Enumeration
 ↓
Identify Attack Surface
 ↓
Initial Access
 ↓
Filesystem Enumeration
 ↓
Objective
```

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Nmap | Reconnaissance and service enumeration |
| Telnet | Remote service connection |
| Kali Linux | Security testing environment |
| Linux CLI | System enumeration |

## 💻 Commands Reference

```bash
ping -c 4 <TARGET_IP>
nmap -sC -sV <TARGET_IP>
telnet <TARGET_IP> 23
whoami
uname -a
pwd
ls
cat <FLAG_FILE>
```

## ⚠️ Disclaimer

This walkthrough was performed in the authorized Hack The Box lab environment.

Use these techniques only against systems you own or have explicit permission to test.

## 👨‍💻 Author

**Karunya Kanth**  
B.Tech CSE — Cybersecurity Student | Sasi Engineering
