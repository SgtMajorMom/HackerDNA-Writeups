![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen?style=flat)
![Tool](https://img.shields.io/badge/Tool-UploadHandler-red?style=flat)
![Tool](https://img.shields.io/badge/Tool-PHPFilterWrapper-red?style=flat)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Platform](https://img.shields.io/badge/Platform-HackerDNA-blue)
![Skill](https://img.shields.io/badge/Skill-BackdoorExploitation-success)
![Skill](https://img.shields.io/badge/Skill-UploadBypass-success?style=flat)


## Objective
Gain initial access to the target by exploiting a vulnerable file upload mechanism, bypassing restrictions, and retrieving the hidden flag.

## Environment
- Platform: HackerDNA
- Tools Used: Nmap, Browser DevTools, Burp Suite (optional), Linux CLI
- Skills Demonstrated: Upload Bypass, Backdoor Exploitation, Enumeration

## Steps Taken
1. Launched the target environment and confirmed connectivity using Nmap to verify the host was reachable.
2. Identified the primary attack surface: a file upload form with visible client-side extension filtering.
3. Used Browser DevTools to inspect the upload request and confirm the server validated only the file extension.
4. Crafted a payload disguised with a permitted extension while embedding executable content.
5. Intercepted the upload request and modified the filename to bypass the extension filter.
6. Uploaded the modified payload and navigated directly to the stored file path.
7. Executed the payload to reveal the protected content and retrieve the flag.

## Discovery
The upload feature blocked common executable extensions but relied solely on superficial validation. DevTools inspection confirmed the server did not validate MIME type or file content. No additional services were exposed, and enumeration confirmed the upload endpoint was the intended entry point.

## Exploitation
By modifying the filename during transit, I bypassed the extension filter and successfully uploaded a malicious file. Direct access to the uploaded file triggered execution, granting access to the hidden flag.

## Flag Retrieval
Once executed, the payload exposed the flag stored behind the upload handler. I captured the flag and submitted it to complete the lab.

## Lessons Learned
- Weak upload validation is a high‑risk vulnerability.
- MIME type and content validation are essential for secure file handling.
- Direct object access to uploaded files can expose sensitive data or
