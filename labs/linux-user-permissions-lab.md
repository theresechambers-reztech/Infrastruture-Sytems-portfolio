# Linux Security & User Management Lab

## Environment
Ubuntu Linux Virtual Machine (VirtualBox)
Bash Shell

## Objective
Understand Linux user identities, authentication storage, group membership, and file permission enforcement.

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
