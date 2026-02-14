# Include Me

## 📝 Overview
This lab demonstrates a basic file inclusion vulnerability. The application loads files based on a user‑controlled parameter, allowing an attacker to request unintended files stored on the server. The goal is to use this behavior to access `flag.txt` and retrieve the lab flag.

All testing was performed inside the authorized HackerDNA lab environment.

---

## 🎯 Objectives
- Identify the parameter used to include files
- Manipulate the parameter to request unintended files
- Access and read `flag.txt`
- Capture and document the flag

---

## 🧰 Tools Used
- Web browser (Chrome/Firefox)
- Browser address bar (manual parameter manipulation)
- PDF viewer (for evidence file)

---

## 🔍 Step 1: Open the Target
I launched the target machine using the IP address provided by the lab.  
The application displayed simple navigation that changed the URL when clicked.

---

## 🕵️ Step 2: Identify the Vulnerable Parameter
By clicking through the interface, I observed the URL contained a parameter such as:


This indicated the application was including files based on user input.

---

## 🧪 Step 3: Test File Inclusion
To test the vulnerability, I replaced the value of the parameter with the name of the file containing the flag:


Pressing Enter caused the application to load and display the contents of `flag.txt`.

---

## 🏁 Step 4: Retrieve the Flag
The flag was displayed directly in the browser.  
I captured a screenshot and documented the exact payload used.

---

## 🛡️ Remediation
To prevent this vulnerability in real applications:

- Do not include files based on unsanitized user input
- Use strict whitelisting for allowed pages
- Block directory traversal sequences (`../`)
- Store sensitive files outside the web root
- Implement server‑side access controls

---

## 📎 Evidence
- `Include-Me.pdf` (uploaded in this folder)  
  Contains screenshots and proof of exploitation.

---

## ✔️ Status
**Lab completed successfully.**  
Flag captured and documented.

