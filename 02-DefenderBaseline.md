# 🛡️ Defender – Ubuntu Server Baseline

## Overview
This document captures the **initial baseline** of the Defender Ubuntu Server VM before applying any hardening or security controls.  
The goal is to record the current network configuration, open ports, services, and system status for later comparison after defenses are applied.

---

## Step 1: VM Startup & Network Verification

-- `ip a` (Verify NAT & Host-Only adapters are up)

![verifyIP](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/1.updateupgrade.png)

- `enp0s3` – NAT adapter (Internet access)
- `enp0s8` – Host-Only adapter (`192.168.27.10/24`)

---

## Step 2: External Nmap Scan (From Kali)

-- `nmap -sV 192.168.27.10`

![nmapScan](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/2.identifynetwork%20.3%20nmap.png)

**Notes:**
- Port 22/tcp (OpenSSH) detected
- No additional services exposed

---

## Step 3: Internal Listening Services

-- `sudo ss -tulpn`

![listeningServices](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/4.listeningsvc.png)

---

## Step 4: Active System Services

-- `sudo systemctl list-units --type=service`

![systemServices](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/5.systemsnap.png)

---

## Step 5: Resource Usage Snapshot

**CPU Usage:**
-- `sar -u 1 5`


**Memory Usage:**
-- `free -h`


**Disk Usage:**
-- `df -h`

![diskUsage](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/5b.%20cpu%2Cmem%2Cdskusage.png)

---

## Step 6: Logging Status

-- `sudo systemctl status rsyslog`

![rsyslogStatus](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/6.rsysbaseline.png)

**Key Log Files:**
- `/var/log/syslog`
- `/var/log/auth.log`

---
