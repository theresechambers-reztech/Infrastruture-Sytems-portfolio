# Linux VM Network Segmentation and Connectivity Testing

## Overview

This lab demonstrates how two Linux virtual machines can communicate over an isolated internal network while remaining separated from external networks.

The exercise focuses on foundational infrastructure skills used in virtualization environments, cloud systems, and enterprise network troubleshooting.

The objective was to:

- configure an internal network between two Linux VMs
- manually assign IP addresses
- verify routing configuration
- test connectivity using ICMP (ping)

---

## Lab Environment

**Platform:**  
VirtualBox

**Operating System:**  
Ubuntu Linux

**Network Type:**  
Internal Network (isolated virtual segment)

**Virtual Machines**

- Server VM
- Client VM

## Commands Used

The following Linux commands were used during the lab to configure networking and test connectivity.


**Configure server IP address**

```
sudo ip addr add 192.168.50.10/24 dev enp0s3
```

**Configure client IP address**

```
sudo ip addr add 192.168.50.20/24 dev enp0s3
```

**Add route to internal network**

```
sudo ip route add 192.168.50.0/24 dev enp0s3
```

**Test connectivity**

```
ping 192.168.50.10
```

## Network Design

Both virtual machines were connected to the same **VirtualBox Internal Network**, allowing communication between the VMs while preventing access to external networks.

Network segment used:

```
192.168.50.0/24
```

Server VM address:

```
192.168.50.10
```

Client VM address:

```
192.168.50.20
```

---

## Configuration Steps

### Step 1 — Prepare two virtual machines

A Linux Operations Lab VM was used as the base system.

A clone of the VM was created so that one machine could act as the **server** and the other as the **client**.

Both machines were connected to the same **VirtualBox Internal Network adapter**.

---

### Step 2 — Configure the internal network adapter

Each VM network adapter was configured with:

```
Adapter Type: Internal Network
Virtual Cable Connected: Enabled
```
### Figure 1 — VirtualBox Internal Network Configuration

<img width="679" height="407" alt="Figure 1 - VirtualBox Internal Network Configuration" src="https://github.com/user-attachments/assets/e18c3716-d5de-4801-8be2-54d372a8c58a" />

This screenshot shows the VirtualBox network adapter configured for **Internal Network mode**, allowing the VMs to communicate on an isolated network segment.

---


This created an isolated network segment where the VMs could communicate privately.

---

### Step 3 — Configure server IP address

On the server VM, the network interface was manually assigned an IP address.

```bash
sudo ip addr add 192.168.50.10/24 dev enp0s3
```

### Figure 2 — Server VM IP Address Configuration

<img width="779" height="463" alt="Figure 2 - IP Address Configuration" src="https://github.com/user-attachments/assets/2aa43a40-fb3b-44c3-9f22-6d68cd3c14bb" />

This screenshot shows the server VM being assigned the IP address `192.168.50.10/24` using the Linux `ip addr` command.

---

---

### Step 4 — Configure client IP address

On the client VM, the interface was manually configured with a different address in the same subnet.

```bash
sudo ip addr add 192.168.50.20/24 dev enp0s3
```

---

### Step 5 — Verify and correct routing

Routing tables were inspected using the Linux `ip route` command.

A route to the internal subnet was added when required.

```bash
sudo ip route add 192.168.50.0/24 dev enp0s3
```

---

### Step 6 — Test connectivity

Connectivity between the client and server VM was verified using ICMP.

```bash
ping 192.168.50.10
```

### Figure 4 — Successful ICMP Connectivity Test

<img width="772" height="456" alt="Figure 3 — Successful ICMP communication between segmented Linux VMs" src="https://github.com/user-attachments/assets/89a71928-2c74-4ca7-8913-98b7beb872c0" />

This screenshot shows the successful ICMP communication between the client and server VM, confirming correct network configuration and connectivity.

---

## Results

The connectivity test produced the following result:

```
8 packets transmitted
8 received
0% packet loss
```

This confirmed that:

- both virtual machines were on the same internal network segment
- IP addressing was correctly configured
- Layer 3 communication between the VMs was successful
- the segmented network was functioning properly

---

## Skills Demonstrated

This lab demonstrates practical experience with:

- Linux networking fundamentals
- manual IP configuration
- virtual machine networking
- network segmentation concepts
- route inspection and correction
- ICMP connectivity testing
- structured network troubleshooting

---

## Security / Infrastructure Insight

Internal network segmentation is commonly used in secure infrastructure environments to isolate systems and limit lateral movement between hosts.

Understanding how to manually configure networking between virtual machines helps build foundational knowledge required for:

- cloud infrastructure architecture
- virtualization platforms
- container networking
- enterprise network troubleshooting
