# 🦌 Hack The Box — Fawn

![Hack The Box](https://img.shields.io/badge/Platform-Hack%20The%20Box-black)
![Difficulty](https://img.shields.io/badge/Difficulty-Very%20Easy-00A4EF)
![Status](https://img.shields.io/badge/Status-Pwned-success)
![Focus](https://img.shields.io/badge/Focus-FTP%20Enumeration-blue)

> Beginner-friendly HTB machine demonstrating FTP enumeration and anonymous access.

## Machine Information

| Field | Details |
|---|---|
| Platform | Hack The Box |
| Machine | Fawn |
| Machine ID | 393 |
| Difficulty | Very Easy |
| OS | Linux |
| Primary Service | FTP |
| Port | 21/TCP |
| Vulnerability | Anonymous FTP access |
| Status | ✅ Pwned |
| Completion | 03 October 2026 |

## Attack Chain

```text
Target
  │
  ▼
Nmap Enumeration
  │
  ▼
TCP/21 — FTP
  │
  ▼
Anonymous Login
  │
  ▼
Directory Enumeration
  │
  ▼
flag.txt discovered
  │
  ▼
get flag.txt
  │
  ▼
✅ PWNED
```

## Walkthrough

### 1. Reconnaissance

```bash
nmap -sC -sV -oN nmap_initial.txt <TARGET_IP>
```

The scan identifies FTP running on TCP port 21.

### 2. Connect to FTP

```bash
ftp <TARGET_IP>
```

Test anonymous authentication:

```text
Username: anonymous
Password: <blank / accepted anonymous password>
```

A successful login indicates that anonymous FTP access is enabled.

### 3. Enumerate Files

Inside the FTP session:

```ftp
ls
dir
pwd
```

The accessible directory contains:

```text
flag.txt
```

### 4. Download the Flag

```ftp
get flag.txt
bye
```

Then read it locally:

```bash
cat flag.txt
```

✅ Flag successfully retrieved.

> The actual flag is intentionally excluded from this public repository.

## Commands

```bash
nmap -sC -sV -oN nmap_initial.txt <TARGET_IP>
ftp <TARGET_IP>
```

Inside FTP:

```ftp
ls
dir
pwd
get flag.txt
bye
```

Local:

```bash
cat flag.txt
```

## Security Analysis

### Finding

Anonymous FTP access allowed unauthenticated users to access files on the server.

### Impact

An attacker able to reach the FTP service could potentially:

- Browse exposed directories
- Download accessible files
- Access sensitive information
- Abuse additional permissions if write access is available

### Defensive Recommendations

- Disable anonymous FTP unless explicitly required.
- Do not store sensitive files in publicly accessible directories.
- Prefer encrypted file-transfer protocols such as SFTP where appropriate.
- Apply least-privilege permissions.
- Restrict unnecessary network exposure.
- Monitor FTP authentication and file-access logs.

## Skills Demonstrated

- Network reconnaissance
- Nmap service enumeration
- FTP enumeration
- Anonymous authentication testing
- File discovery
- File retrieval
- Linux command line
- Security documentation

## Evidence

Add screenshots to `screenshots/`:

```text
01-nmap-scan.png
02-ftp-login.png
03-directory-listing.png
04-download-flag.png
05-final-result.png
```

## Completion

**Machine:** Fawn  
**HTB Machine ID:** 393  
**Status:** ✅ Pwned  
**Completed:** 03 October 2026

## Disclaimer

This walkthrough documents activity performed in the authorized Hack The Box environment. Use these techniques only on systems you own or have explicit permission to test.
