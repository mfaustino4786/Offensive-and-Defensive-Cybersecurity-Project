# Offensive-and-Defensive-Cybersecurity-Project
 Overview
This repository documents my personal **Red vs Blue cybersecurity lab** — a simulated corporate network environment designed to practice **offensive** and **defensive** security skills.  
The goal of this project is to replicate real-world scenarios, execute attack simulations, and develop security controls to detect, mitigate, and respond to threats.

---

 🎯 Objectives
- Simulate realistic cyber attacks (Red Team)
- Harden systems and deploy defenses (Blue Team)
- Develop and test incident response playbooks
- Document findings, improvements, and lessons learned

---

🖥️ Lab Architecture

| Role         | OS / Tools Used                                        | IP Address     |
|--------------|--------------------------------------------------------|----------------|
| **Attacker** | Kali Linux (Nmap, Metasploit, John the Ripper)          | 192.168.27.5   |
| **Victim**   | Metasploitable 2 (vulnerable Linux target)              | 192.168.27.4   |
| **Defender** | Ubuntu Server (UFW firewall, fail2ban, IDS/IPS)         | 192.168.27.10  |

## 🔗 Lab Sections

1. [Simulated Attack](SimulatedAttack.md)
2. [Defender Baseline](DefenderBaseline.md)
3. [Hardening](Hardening.md)
   
## ⚔️ Red Team Activities
- **Reconnaissance:** Nmap scanning for open ports & services
- **Exploitation:** Using Metasploit to gain shell access
- **Post-Exploitation:** Dumping `/etc/passwd` and `/etc/shadow` files
- **Password Cracking:** Using `John the Ripper` and `hashcat`
- **Persistence:** Establishing backdoors

---

## 🛡️ Blue Team Activities
- **System Hardening:** Removing unused services, updating packages
- **Firewall Rules:** UFW and iptables configurations
- **Intrusion Detection:** Installing and tuning Snort/Suricata
- **Log Analysis:** Reviewing `/var/log` for suspicious activity
- **Incident Response:** Blocking attacker IPs, restoring services

---

## 🛠 Tools & Technologies
- **Offense:** Nmap, Metasploit, Hydra, John the Ripper
- **Defense:** UFW, fail2ban, Snort, Wireshark
- **Utilities:** netcat, tcpdump, OpenVAS








## 📅 Progress Log
- **08/09/2025** Initial lab setup in VirtualBox
- **08/10/2025** Performed reconnaissance and scanning with Nmap
- **08/10/2025** Gained shell access to Metasploitable via FTP exploit
- **08/10/2025** Extracted password hashes and began cracking
- **08/11/2025** Implemented UFW firewall rules on Ubuntu defender
