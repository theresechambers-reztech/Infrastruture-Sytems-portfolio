# Linux Firewall and SSH Hardening Lab

## Lab Overview

This lab demonstrates basic Linux infrastructure security by installing and securing an SSH service using the Ubuntu Uncomplicated Firewall (UFW).

The objective was to observe network services, introduce a remote access service, and then implement firewall rules to control system exposure.

---

## Lab Environment

- Ubuntu Linux VM
- VirtualBox virtualization environment
- Local terminal access
- GitHub repository documentation

---

## Objective

Demonstrate fundamental Linux security operations including:

- service exposure identification
- SSH server installation
- firewall rule configuration
- port protection
- verification of network security posture

---

## Step 1 – Inspect Listening Network Services

The system was inspected for active listening ports.

Command used:

```
ss -tuln
```

Initial inspection showed no SSH service running.

---

## Step 2 – Install OpenSSH Server

SSH was installed to enable remote access.

Command used:

```
sudo apt install openssh-server
```

After installation, SSH began listening on port 22.

Verification command:

```
ss -tuln
```

Result:

```
tcp LISTEN 0.0.0.0:22
tcp LISTEN [::]:22
```

### Screenshot – SSH Service Listening on Port 22

<img width="769" height="448" alt="01-port-22-listening" src="https://github.com/user-attachments/assets/21151bff-3fe1-4f89-9103-e58962b57b7b" />


This confirmed the SSH service was listening on both IPv4 and IPv6 interfaces.

---

## Step 3 – Check Firewall Status

Firewall status was inspected.

Command used:

```
sudo ufw status
```

Result:

```
Status: inactive
```

This confirmed the firewall was installed but not yet active.

---

## Step 4 – Allow SSH Through Firewall

Before enabling the firewall, SSH traffic was allowed to prevent accidental lockout.

Command used:

```
sudo ufw allow ssh
```

Result:

```
Rules updated
Rules updated (v6)
```

---

## Step 5 – Enable the Firewall

The firewall was activated.

Command used:

```
sudo ufw enable
```

Result:

```
Firewall is active and enabled on system startup
```
### Screenshot – Firewall Activation

<img width="764" height="459" alt="02-firewall-enabled" src="https://github.com/user-attachments/assets/d6d0083e-d14d-47f4-80bf-c1207580899d" />


---

## Step 6 – Verify Firewall Rules

Firewall configuration was verified.

Command used:

```
sudo ufw status verbose
```

Result:

```
Status: active

Default: deny (incoming), allow (outgoing)

22/tcp ALLOW IN Anywhere
22/tcp (v6) ALLOW IN Anywhere (v6)
```

### Screenshot – Firewall Rules Verification

<img width="765" height="456" alt="03-firewall-rules-verification" src="https://github.com/user-attachments/assets/608f3dfd-a40d-4d6a-8d11-8233310720a6" />


This confirms that:

- SSH access is permitted
- all other inbound traffic is blocked

---

## Step 7 – Test Internet Connectivity

After enabling the firewall, outbound connectivity was tested to ensure normal network operation.

Command used:

```
ping 8.8.8.8
```

Result:

```
6 packets transmitted, 6 received, 0% packet loss
```

This confirms that outbound traffic is still permitted while inbound traffic remains restricted by the firewall.


### Screenshot – Successful Connectivity Test

<img width="769" height="466" alt="04-ping-8 8 8 8-successful" src="https://github.com/user-attachments/assets/4fc4f785-9491-46f2-851c-8cf1de4389b4" />


---

## Verification and Testing

Evidence of the lab steps was captured through screenshots including:

- SSH service listening on port 22
- firewall activation
- firewall rule verification
- successful outbound connectivity test

---

## Outcome

This lab demonstrated the following Linux infrastructure operations:

- network service inspection
- SSH server installation
- firewall configuration
- port exposure management
- firewall rule verification
- outbound connectivity testing

---

## Security / Infrastructure Insight

Installing network services introduces potential attack surfaces.  
Firewall rules must be implemented to restrict system exposure and allow only necessary services.

A secure baseline configuration for Linux servers typically includes:

- default deny policy for inbound traffic
- explicit allow rules for required services
- firewall enabled at system startup
- verification of connectivity after firewall implementation

This approach significantly reduces system attack surface while maintaining required functionality.
