# Linux Security & User Management Lab

## Environment
Ubuntu Linux Virtual Machine (VirtualBox)
Bash Shell

## Objective
Understand Linux user identities, authentication storage, group membership, and file permission enforcement.

## User Identity Verification

Commands used:

whoami
id
sudo whoami

Purpose:

These commands verify the current user identity, display the user and group IDs, and demonstrate privilege escalation using sudo.

<img width="763" height="445" alt="01-user-identity" src="https://github.com/user-attachments/assets/fe6d8391-eb99-420d-8ad9-d49a437770bb" />

## User Switching

Commands used:

ls /home
su - analyst
whoami
pwd

Purpose:

This demonstrates switching between users and confirms the current working directory and active user context.

<img width="734" height="450" alt="02-user-switching" src="https://github.com/user-attachments/assets/71e80cb6-3cd2-4cc5-a3be-5a3600c7a2d4" />

## Authentication File Protection

Commands used:

cat /etc/shadow
sudo cat /etc/shadow

Purpose:

This demonstrates that the /etc/shadow file containing password hashes is protected and accessible only with root privileges.

<img width="762" height="459" alt="03-authentication-files" src="https://github.com/user-attachments/assets/22b9ee5b-ccba-43be-b04e-2a9bf8f998c3" />

## File Permission Enforcement

Commands used:

chmod 000 test.txt
ls -l
cat test.txt

Purpose:

This demonstrates how Linux file permissions can prevent access even for the file owner when all permissions are removed.

<img width="769" height="457" alt="04-chmod-permissions" src="https://github.com/user-attachments/assets/04783ca5-4c85-4789-af51-d1210aaba164" />


## Lab Activities

Created and switched Linux users to examine privilege boundaries.

Investigated Linux authentication files including passwd, shadow, and group system files to understand password storage and access protections.

Compared user identities and group membership using the id command.

Practiced file permission analysis using ls -l.

Tested permission enforcement using chmod 600 and chmod 000 to observe owner, group, and others permission behavior.

Verified security enforcement when attempting to access restricted files.

Inspected special permission behavior by reviewing the SUID configuration on the Linux password management program.

## Commands Practiced

whoami  
id  
su  
pwd  
ls -la  
ls -l  
cat passwd  
cat group  
sudo cat shadow  
touch  
chmod  
ls -l passwd

## Key Learning Outcomes

Linux enforces strict separation between users and administrative privileges.

Password hashes are protected and require elevated privileges to view.

File permissions can prevent access even for the file owner when permissions are removed.

Special permission bits such as SUID allow specific programs to run securely with elevated privileges when required.
## SUID Permission Example

Command used:

ls -l /usr/bin/passwd

Output:

-rwsr-xr-x 1 root root ...

The "s" in the owner permissions indicates the Set User ID (SUID) bit is enabled.

This means the program executes with root privileges even when run by a normal user.

This mechanism allows the passwd program to modify protected authentication files such as /etc/shadow while still being executed by a normal user.

<img width="766" height="453" alt="05-suid-passwd" src="https://github.com/user-attachments/assets/ce06e032-ff8c-4034-a8f4-f7bdbec639db" />
