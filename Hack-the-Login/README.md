![Difficulty: Very Easy](https://img.shields.io/badge/Difficulty-Very%20Easy-brightgreen?style=flat)
![Tool](https://img.shields.io/badge/Tool-Nmap-red)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Platform](https://img.shields.io/badge/Platform-HackerDNA-blue)
![Skill](https://img.shields.io/badge/Skill-Enumeration-success)
# Hack the Login

**Platform:** HackerDNA  
**Difficulty:** Very Easy  
**Objective:** Bypass the login page by inspecting the client-side script and retrieve the flag.

## Steps

1. Start the machine in HackerDNA.
2. Click the provided lab URL.
3. When the login page loads, press **F12** to open Developer Tools.
4. Go to **Sources → script.js**.
5. Inside the script, locate:
   - Username
   - Password
   - Flag reference
6. Log in using the credentials found in the script.
7. Enter the flag shown in the script or referenced file.
8. Submit the flag to complete the lab.


