# Anonymous  
**Platform:** HackerDNA  
**Difficulty:** Easy  
**Points:** 10  

## Objective  
This version of the Anonymous lab demonstrates how insecure configurations in legacy services like FTP can expose sensitive information. Although the web server appears empty, an underlying FTP service is accessible and misconfigured.

Your goal is to:

- Identify the exposed service  
- Authenticate using anonymous FTP access  
- Retrieve the flag  
- Understand why this misconfiguration is dangerous  

## Vulnerability Summary  
The target machine exposes an FTP service that allows login with:

- **Username:** anonymous  
- **Password:** *(blank)*  

Once authenticated, the server provides access to sensitive files, including the flag.  
The issue stems from:

- Anonymous FTP access enabled  
- No directory restrictions  
- Flag stored in a publicly accessible location  
- Active Mode FTP is causing client‑side transfer failures  

## Steps Taken

### 1. Initial Recon  
Navigating to the target IP displayed a simple message:

> *Server is Running — There is nothing to see here.*

The web server is a decoy. Enumeration attempts (directories, files, DevTools) revealed nothing.  
The real vulnerability is exposed on a different port.

### 2. Anonymous FTP Login  
Using PowerShell, I connected to the FTP service:
ftp <target-ip>
User: anonymous
Password: (blank)
230 Login successful.


This confirmed anonymous FTP access was enabled.

### 3. Active Mode Failure  
Attempting to download the flag using the built‑in FTP client resulted in:

425 Failed to establish connection


This occurs because Windows FTP defaults to **Active Mode**, which requires the server to open a connection back to the client—blocked by Windows Firewall.

### 4. Pivot to PowerShell WebClient (Passive Mode)  
PowerShell’s `WebClient` uses **Passive Mode** by default, allowing the client to initiate the connection and bypass firewall restrictions.

```powershell
$url = "ftp://<target-ip>/flag.txt"
$wc = New-Object System.Net.WebClient
$wc.DownloadFile($url, "$home\Downloads\flag.txt")
```   ← THIS closes the code block

### 5. Retrieve the Flag
Once downloaded:
```powershell
Get-Content "$home\Downloads\flag.txt"



The flag is displayed and ready for submission.

Common Pitfalls
Enumerating the web server — it’s intentionally empty.

Using the built‑in FTP client — Active Mode causes transfer failures.

Running PowerShell commands inside the FTP shell — they won’t execute.

What I Learned
How to recognize when a web server is a decoy

How to identify exposed services beyond HTTP

Differences between Active vs. Passive FTP

How to use PowerShell to retrieve files from FTP

How to troubleshoot failed transfers

How to pivot quickly when a tool or protocol fails
