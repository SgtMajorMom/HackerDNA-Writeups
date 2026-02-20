![Tool](https://img.shields.io/badge/Tool-Nmap-red)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Platform](https://img.shields.io/badge/Platform-HackerDNA-blue)
![Skill](https://img.shields.io/badge/Skill-Enumeration-success)

Spoof! — HackerDNA Lab Writeup
Author: Dorothy Spencer
Date: 02/16/2026
Platform: HackerDNA
Difficulty: Easy
Points: 10 (+5 for community writeup)

Objective
This lab demonstrates how insecure trust in client‑supplied HTTP headers can lead to Broken Access Control. The target application restricts administrative access to “internal” company users based on IP address. By spoofing the X‑Forwarded‑For header, we can bypass the IP check and retrieve the flag without authentication.

Vulnerability Description
The application incorrectly relies on the X‑Forwarded‑For header to determine whether a user is connecting from the internal network. Because this header is fully client‑controlled, it cannot be trusted for security decisions.

“The server only allowed ‘internal’ company users to access the administrative area without a password.”
“The application suffers from Broken Access Control due to insecure trust in user-supplied HTTP headers.”

This makes the IP validation entirely bypassable.

Target Information
When the machine starts, the lab provides a target IP.
In my lab, the target was 3.249.64.170 and also a reload of server lab of 108.130.178.159

When visiting the target, the page displays:

Your IP: 74.129.248.153

Required internal network IP: 108.130.178.159

Message: “You are not connecting from company network… Password is required for external access.”

This reveals the exact IP you must spoof.

Understanding the Client‑Side Logic
The page itself exposes the vulnerability:

“This lab is NOT about a login script. It’s about spoofing your IP address check, which is happening client-side.”

The browser displays:

My real IP

The internal IP required

A password prompt that only appears for “external” users

This confirms the access control decision is based solely on the IP value the client presents.

Exploit Method: Spoofing the IP
I used PowerShell (not CMD) because it handled the header correctly.
Code Used: curl.exe -L -H "X-Forwarded-For: 108.130.178.159" http://108.130.178.159

This overrides your real IP and presents the trusted internal IP to the server.

Why PowerShell?
CMD often breaks header formatting.
PowerShell reliably sends the header exactly as written.

Flag Retrieval
Running the spoofed curl request returned the flag immediately: 5 ******* **** **** *********** d
The server treated me as an internal user and granted access without requiring a password.

Submitting the Flag
You then returned to the HackerDNA interface and submitted the flag:

“Copy that code as it appeared and paste in the designated field in the lab.”

Flag earned: +10 pts


