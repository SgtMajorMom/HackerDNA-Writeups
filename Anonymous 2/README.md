Anonymous 2 — vsftpd 2.3.4 Backdoor Exploitation
A walkthrough of the Anonymous 2 lab from HackerDNA, demonstrating enumeration, identification, and exploitation of the intentionally backdoored vsftpd 2.3.4 service. This challenge highlights how a compromised software distribution can provide attackers with immediate root access through a crafted username.

Note: The lab assigns new IPs each time it launches. All IPs in this repository use <FTP_IP> and <WEB_IP> placeholders for clarity and reproducibility.

🧭 Lab Summary
This lab focuses on exploiting a malicious backdoor embedded in vsftpd 2.3.4, a version distributed after attackers compromised the official source. When a username ending in :) is submitted, the service opens a remote shell on port 6200. The goal is to identify the vulnerable service, trigger the backdoor, and retrieve the flag from the resulting root shell.

🎯 Objectives
Enumerate exposed services

Identify the vulnerable vsftpd version

Trigger the backdoor using a crafted username

Connect to the spawned shell

Locate and read the flag

📂 Repository Contents
Anonymous 2.pdf — Full polished writeup with screenshots

Anonymous 2.docx — Working notes and draft version

README.md — Overview and context for the repository

🛠️ Tools & Techniques
nmap for service enumeration

Gobuster for optional web directory discovery

nc (Netcat) for triggering the backdoor and connecting to the shell

Linux privilege confirmation and file discovery commands

🔍 Key Takeaways
vsftpd 2.3.4 is intentionally backdoored and should never be used in production environments.

A single compromised package can grant instant root access with minimal interaction.

Silent shells require confidence and methodical command execution.

Enumeration confirms the attack path, but exploitation is straightforward once the version is identified.
