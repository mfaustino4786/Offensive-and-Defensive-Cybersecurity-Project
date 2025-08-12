# 🛡️ Defender – Ubuntu Server Baseline

## Overview
This document captures the **initial baseline** of the Defender Ubuntu Server VM before applying any hardening or security controls.  
The goal is to record the current network configuration, open ports, services, and system status for later comparison after defenses are applied.

---

## Step 1: VM Startup & Network Verification

-- `ip a` (Verify NAT & Host-Only adapters are up)

![verifyIP](screenshots/baseline-verify-ip.png)

- `enp0s3` – NAT adapter (Internet access)
- `enp0s8` – Host-Only adapter (`192.168.27.10/24`)

---

## Step 2: External Nmap Scan (From Kali)

-- `nmap -sV 192.168.27.10`

![nmapScan](screenshots/baseline-nmap.png)

**Notes:**
- Port 22/tcp (OpenSSH) detected
- No additional services exposed

---

## Step 3: Internal Listening Services

-- `sudo ss -tulpn`

![listeningServices](screenshots/baseline-ss.png)

---

## Step 4: Active System Services

-- `sudo systemctl list-units --type=service`

![systemServices](screenshots/baseline-systemctl.png)

---

## Step 5: Resource Usage Snapshot

**CPU Usage:**
-- `sar -u 1 5`

![cpuUsage](screenshots/baseline-cpu.png)

**Memory Usage:**
-- `free -h`

![memUsage](screenshots/baseline-memory.png)

**Disk Usage:**
-- `df -h`

![diskUsage](screenshots/baseline-disk.png)

---

## Step 6: Logging Status

-- `sudo systemctl status rsyslog`

![rsyslogStatus](screenshots/baseline-rsyslog.png)

**Key Log Files:**
- `/var/log/syslog`
- `/var/log/auth.log`

---

## Step 7: Observations
- Minimal services running by default
- Only SSH exposed externally
- Logging service active and capturing system events

---

✅ **Next Step:** Proceed to [After Hardening Report](after_hardening.md) to compare system state after implementing security controls.
