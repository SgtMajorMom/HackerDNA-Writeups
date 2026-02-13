# Secrets in the Source 2

## 📝 Overview
This lab focuses on identifying sensitive information that has been accidentally exposed within the application's source code. The goal is to locate the leaked secret, understand why it is a security risk, and retrieve the flag.

All testing was performed in an authorized HackerDNA lab environment.

---

## 🎯 Objectives
- Review the application’s source code for exposed secrets  
- Identify hardcoded credentials, tokens, or sensitive values  
- Use the discovered secret to access restricted functionality  
- Capture the lab flag  
- Document findings and remediation steps  

---

## 🧰 Tools Used
- Web browser (Chrome/Firefox)  
- Browser DevTools (View Source / Inspect Element)  
- PDF viewer (for evidence file)  

---

## 🔍 Step 1: Initial Exploration
I began by loading the target application and reviewing the visible interface.  
Nothing sensitive appeared on the main page, so I proceeded to inspect the source code.

---

## 🕵️ Step 2: Inspecting the Source Code
Using **View Page Source** or **Inspect Element**, I searched for:

- Hardcoded API keys  
- Hidden fields  
- Comments left by developers  
- Embedded credentials  

During this review, I located a sensitive value that should not have been exposed.

---

## 🔑 Step 3: Using the Exposed Secret
The discovered secret allowed access to a restricted area of the application.  
After submitting or applying the secret, the application revealed the protected


(Replace this with your actual flag.)

---

## 🛡️ Remediation
To prevent this issue in real-world applications:

- Never store secrets in client-side code  
- Use environment variables or secure vaults for sensitive data  
- Remove debugging comments before deployment  
- Implement server-side access controls  
- Rotate any exposed keys immediately  

---

## 📎 Evidence
- `Secrets-in-the-Source-2.pdf` (uploaded in this folder)  
  Contains screenshots and step-by-step proof of exploitation.

---

## ✔️ Status
**Lab completed successfully.**  
Flag captured and documented.
