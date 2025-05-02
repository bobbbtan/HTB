Walkthrough for Privilege Escalation Module

Step 1: SSH Access to Target Machine
Start by accessing the machine via SSH using the given username and port:
 
![image](https://github.com/user-attachments/assets/8eb5e7d8-f844-4723-8bfe-37bfa260042c)

Step 2: Check User Permissions with sudo -l
Once logged in, list the allowed sudo commands: 
![image](https://github.com/user-attachments/assets/38db9461-8e92-4e87-8d13-cd0ffdcf0a2a)

Step 3: Retrieve User-Level Flag
Check your identity and current working directory, navigate to user2’s home directory and read the user-level flag: 


![image](https://github.com/user-attachments/assets/229cfea1-c44c-47d2-a59b-2575d2688d3a)




Step 4: Attempt Root Access
Try to access the root flag: 
![image](https://github.com/user-attachments/assets/7f14c8e4-2cff-4a31-b6f5-dc45f66479c3)

Step 5: Investigate Permissions and SSH Keys
List all files and their permissions: 
![image](https://github.com/user-attachments/assets/d2892f63-9f25-4b64-bcf2-58e63d59f05d)

List all the files and permissions:
 
![image](https://github.com/user-attachments/assets/6694968d-dc1e-4900-b68c-7aadc0773bcb)







Cat rsa id
 ![image](https://github.com/user-attachments/assets/ac4f59fb-bd96-48bb-aa64-a9e1cd9d86c5)


Step 6: Set Up SSH Key for Root Access
1.	Open a new terminal and create a new file:
 ![image](https://github.com/user-attachments/assets/aa4edcfb-0cb0-4b0b-a9f1-352a5d733758)

 
2.	Paste the private key content into it and save.
3.	Change permissions to secure the key:
 ![image](https://github.com/user-attachments/assets/4c8ffc5d-8f84-4bc7-b41f-fb0df57b6b59)


4.	Use the private key to SSH as root: 

Then, we got the flag
 ![image](https://github.com/user-attachments/assets/5e5647b0-333b-4922-b016-2c4c85e497cd)

 
🛡️ CVSS Assessment of the Vulnerability
Based on the vulnerability identified in this privilege escalation exercise, I assessed its severity using the CVSS v3.1 standard.
In this case, the attacker was able to escalate privileges from a normal user to root by reading the private SSH key (id_rsa) due to misconfigured file permissions. This allowed full root access through SSH.
I used the CVSS calculator from FIRST.org and filled in the values based on the situation:
•	Attack Vector (AV): Network – because the attack is carried out over SSH.
•	Attack Complexity (AC): Low – the attacker doesn’t need special conditions.
•	Privileges Required (PR): Low – initial access as a user is enough.
•	User Interaction (UI): None – no interaction from another user is needed.
•	Scope (S): Unchanged – the vulnerability doesn’t affect other systems.
•	Confidentiality (C): High – attacker gains access to all data.
•	Integrity (I): High – attacker can modify any files as root.
•	Availability (A): High – attacker can stop services or delete files.
After entering these values, the calculator gave a CVSS score of 8.8, which is considered High.
 
![image](https://github.com/user-attachments/assets/6f0c90ba-05fb-44f7-b6fe-4090608f0a03)

