Phase 2 – System Hardening (Defender)

Step 1: Update & Patch System

sudo apt update && sudo apt upgrade -y

![screenshotupdate](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/01h.updateupgrade.png)
Step 2: Configure UFW Firewall

sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
sudo ufw status verbose

![install](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/02.enableconfigfirewall.png)
Step 3: Install & Configure Fail2Ban

sudo apt install fail2ban -y
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
sudo nano /etc/fail2ban/jail.local

![installfail](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/03.fail2ban.png)
In jail.local:

[sshd]
enabled = true
port    = ssh
logpath = %(sshd_log)s
maxretry = 5
bantime = 3600

sudo systemctl enable fail2ban
sudo systemctl start fail2ban
sudo fail2ban-client status sshd

![configjail](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/03b.jail.local2.png)
Step 4: Install & Configure Suricata (IDS/IPS)

![install](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/04.installsuricata.png)

sudo apt install suricata -y
sudo systemctl enable suricata
sudo systemctl start suricata
sudo suricata-update
sudo systemctl restart suricata
sudo systemctl status suricata

![configsuri](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/04.configsuricata.png)
Step 5: Disable Root SSH Login

sudo nano /etc/ssh/sshd_config

Set:

PermitRootLogin no

sudo systemctl restart ssh

![disablerootssh](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/05.disablerootssh.png)
Summary

In this phase, we:

    Applied all available updates & patches.

    Configured UFW to block all inbound traffic except approved ports.

    Enabled Fail2Ban to prevent brute force SSH logins.

    Installed and configured Suricata for intrusion detection.

    Disabled root SSH login for improved access control.
