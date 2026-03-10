# Linux System Monitoring & Network Inspection Lab

## Objective
Practice core Linux operational commands used to inspect running processes, monitor system activity, identify network interfaces, review routing information, inspect sockets, and test connectivity in an Ubuntu VirtualBox environment.

## Environment Setup
- Ubuntu Linux Virtual Machine
- Oracle VirtualBox
- Bash terminal
- Personal non-production lab environment

## Commands Used
```
whoami
ps
ps aux
top
sleep 300
ps aux | grep sleep
kill 3317
ip a
ip route
ping 10.0.2.2
ping 8.8.8.8
ss
```

## Configuration Steps

### 1. Verify the current user
Command:
```
whoami
```

### 2. View running processes for the current terminal
Command:
```
ps
```

This displayed processes associated with the active terminal session.

### 3. View all system processes
Command:
```
ps aux
```

This displayed system-wide processes including user processes and background services.

### 4. Monitor system activity in real time
Command:
```
top
```

This displayed CPU usage, memory usage, active tasks, and system load in real time.

### 5. Create a test process
Command:
```
sleep 300
```

This created a temporary process designed to run for five minutes.

### 6. Identify the running process
Command:
```
ps aux | grep sleep
```

This displayed both the **sleep 300** process and the **grep sleep** command used to search for it.

### 7. Terminate the process
Command:
```
kill 3317
```

The terminal running the sleep command immediately returned a **Terminated** message, confirming successful process termination.

### 8. Inspect network interfaces
Command:
```
ip a
```

Observed interfaces:
- `lo` loopback interface
- `enp0s3` primary VM network interface

Observed IP address assigned to the VM:
`10.0.2.15`

### 9. Review routing information
Command:
```
ip route
```

Observed routing entries:
```
default via 10.0.2.2 dev enp0s3 proto dhcp src 10.0.2.15 metric 100
10.0.2.0/24 dev enp0s3 proto kernel scope link src 10.0.2.15 metric 100
```

This indicated that outbound traffic is routed through gateway **10.0.2.2** using interface **enp0s3**.

### 10. Test connectivity to the gateway
Command:
```
ping 10.0.2.2
```

Observed repeated responses:
```
64 bytes from 10.0.2.2
```

The command was stopped using **Ctrl + C**.

### 11. Test external internet connectivity
Command:
```
ping 8.8.8.8
```

Observed ping statistics:
- 27 packets transmitted
- 27 received
- 0% packet loss

This confirmed successful internet connectivity from the VM.

### 12. Inspect network sockets
Command:
```
ss
```

Observed output columns:
- Netid
- State
- Recv-Q
- Send-Q
- Local Address:Port
- Peer Address:Port
- Process

## Verification / Testing
The lab was verified by successfully:

- displaying running processes using `ps` and `ps aux`
- monitoring system activity with `top`
- creating a `sleep 300` process
- locating the process using `ps aux | grep sleep`
- terminating the process using `kill`
- identifying network interfaces using `ip a`
- reviewing routing information using `ip route`
- successfully pinging gateway `10.0.2.2`
- successfully pinging `8.8.8.8` with **0% packet loss**
- displaying socket information using `ss`

## Outcome
This lab demonstrated foundational Linux operational skills including:

- process monitoring
- process identification
- process termination
- system activity monitoring
- network interface inspection
- routing table inspection
- connectivity testing
- socket inspection

## Security / Infrastructure Insight
Process monitoring tools such as `ps` and `top` allow administrators to detect abnormal activity and identify resource-intensive processes. Network inspection tools such as `ip`, `ss`, and `ping` help validate network configuration and confirm connectivity between systems, gateways, and external networks.

## Real-World Application
These commands are commonly used in Linux system administration and infrastructure troubleshooting to diagnose performance issues, inspect system processes, verify routing configuration, confirm connectivity to network gateways, and validate external internet access.
