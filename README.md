# SOC Analyst Home Lab

## Project Overview

This project demonstrates the setup and configuration of a beginner cybersecurity home lab using VirtualBox. The lab environment consists of three virtual machines running Kali Linux, Ubuntu Server, and Windows 10 connected through a NAT Network for secure internal communication and internet access.

The purpose of this lab is to practice:
- Virtualization
- Networking fundamentals
- Linux and Windows administration
- Basic security monitoring
- Network scanning and reconnaissance
- Packet analysis
- Troubleshooting connectivity and firewall issues

This project was created as part of hands-on cybersecurity and SOC Analyst training.

---

# Lab Architecture

## Virtual Machines

| Machine | Operating System | Purpose | IP Address |
|---|---|---|---|
| Kali Linux | Kali Linux | Attacker / Security Testing Machine | 10.0.2.5 |
| Ubuntu Server | Ubuntu Server | Linux Target Server | 10.0.2.4 |
| Windows 10 | Windows 10 Enterprise Evaluation | Windows Monitoring Target | 10.0.2.15 |

---

# Network Configuration

All virtual machines were connected to the same VirtualBox NAT Network to allow:
- Communication between VMs
- Internet connectivity
- Isolation from the host machine’s main network

## Networking Details

| Setting | Configuration |
|---|---|
| Network Type | NAT Network |
| DHCP Enabled | Yes |
| Virtualization Platform | VirtualBox |

---

# Network Diagram

<img width="561" height="361" alt="Network" src="https://github.com/user-attachments/assets/74124eac-daa9-4038-9762-eaec20639cd9" />

---

# Tools and Technologies Used

## Virtualization
- VirtualBox

## Operating Systems
- Kali Linux
- Ubuntu Server
- Windows 10 Enterprise Evaluation

## Security and Networking Tools
- Nmap
- Wireshark
- OpenSSH
- Windows Event Viewer
- Windows Defender Firewall

---

# Virtual Machine Configuration

## Kali Linux VM
| Setting | Value |
|---|---|
| RAM | 2 GB |
| CPU | 2 Cores |
| Storage | 30 GB |

### Purpose
Used as the primary attacker and security testing machine for:
- Network scanning
- Service enumeration
- SSH access
- Packet capture

### Screenshot

<img width="1219" height="844" alt="image" src="https://github.com/user-attachments/assets/35aade67-137e-4f75-9ccf-83c94d3e7c81" />


---

## Ubuntu Server VM
| Setting | Value |
|---|---|
| RAM | 2 GB |
| CPU | 1-2 Cores |
| Storage | 20 GB |

### Purpose
Used as a Linux server target for:
- SSH access
- Service hosting
- Linux administration practice

### Installed Services
- OpenSSH Server
- Apache2

### Screenshot

<img width="1078" height="676" alt="ubuntu-server" src="https://github.com/user-attachments/assets/f366f653-6c60-4b8e-b9b0-d49db4db8ab0" />

---

## Windows 10 VM
| Setting | Value |
|---|---|
| RAM | 4 GB |
| CPU | 2 Cores |
| Storage | 50 GB |

### Purpose
Used as a Windows enterprise endpoint for:
- Event log monitoring
- Firewall configuration
- Connectivity troubleshooting
- Security monitoring practice

### Screenshot

<img width="1206" height="755" alt="windows10" src="https://github.com/user-attachments/assets/50cb8a65-fb7f-42df-88d0-afd78b548169" />

---

# Setup Process

## Step 1 — Install VirtualBox

VirtualBox was installed on the host system along with the VirtualBox Extension Pack.

---

## Step 2 — Download Operating Systems

The following operating systems were downloaded and installed:
- Kali Linux
- Ubuntu Server
- Windows 10 Enterprise Evaluation

---

## Step 3 — Create Virtual Machines

Three separate virtual machines were created and configured with appropriate:
- RAM
- CPU allocation
- Virtual storage
- Network settings

---

## Step 4 — Configure NAT Network

A NAT Network was created in VirtualBox and assigned to all virtual machines.

### Configuration Steps
1. Opened VirtualBox Network Manager
2. Created a new NAT Network
3. Enabled DHCP
4. Attached all VMs to the same NAT Network

<img width="1920" height="1032" alt="Vbox-setup" src="https://github.com/user-attachments/assets/05f46cfa-19ae-45f6-84cd-bf56810f341a" />

---

# Connectivity Testing

Connectivity between systems was tested using ping commands.

## Ping Test from Kali to Ubuntu

<img width="1219" height="844" alt="ubuntu-ping" src="https://github.com/user-attachments/assets/277882cd-f74f-4832-b9e4-dd4225103c3c" />

---

## Ping Test from Kali to Windows

Initially, Windows did not respond to ping requests due to Windows Defender Firewall blocking ICMP Echo Requests.

The issue was resolved by enabling:
- File and Printer Sharing (Echo Request - ICMPv4-In)

inside Windows Defender Firewall.

### Screenshot

<img width="1206" height="755" alt="windows-firewall-rule" src="https://github.com/user-attachments/assets/a303aecf-da2f-46e1-bca5-a2ba5353429c" />


### Screenshot

<img width="1222" height="844" alt="windows-ping" src="https://github.com/user-attachments/assets/b9fa715f-5596-431d-a0e6-42241ee28e69" />

---

# Network Scanning

## Nmap Scan from Kali

Nmap was used to identify:
- Open ports
- Running services
- Operating system information

### Command Used

```bash
nmap -sV <target-ip>
```

### Screenshot

<img width="1222" height="844" alt="nmap-results" src="https://github.com/user-attachments/assets/39016d01-bacb-401e-9489-444f2ef80ccf" />

---

# SSH Connectivity Testing

SSH access from Kali Linux to Ubuntu Server was successfully configured and tested.

### Command Used

```bash
ssh username@<ubuntu-ip>
```

### Screenshot

<img width="1390" height="941" alt="ssh-results" src="https://github.com/user-attachments/assets/a5c6c492-0d7f-4082-8375-859c2891a0d8" />

---

# Packet Analysis

Wireshark was used to capture and analyze:
- ICMP traffic
- SSH traffic
- TCP/IP communication

### Screenshot

INSERT WIRESHARK CAPTURE SCREENSHOT HERE

---

# Windows Event Viewer Monitoring

Windows Event Viewer was used to review:
- Security logs
- System logs
- Application logs

This helped in understanding:
- Login events
- Service activity
- System behavior

### Screenshot

<img width="1206" height="755" alt="event-viewer-logs" src="https://github.com/user-attachments/assets/a5ffff5f-18ac-4456-b088-7a7975d526df" />

---

# Skills Learned

Through this project, the following skills were developed and strengthened:

## Virtualization
- Creating and managing virtual machines
- Resource allocation
- Snapshot management

## Networking
- NAT networking
- IP addressing
- Connectivity troubleshooting
- ICMP and TCP/IP fundamentals

## Linux Administration
- SSH configuration
- Package installation
- Service management

## Windows Administration
- Windows Defender Firewall configuration
- Event Viewer analysis
- Basic endpoint monitoring

## Security Operations
- Network scanning
- Reconnaissance
- Packet capture analysis
- Security troubleshooting

---

# Challenges Faced

## Windows Ping Failure

### Issue
The Windows VM did not initially respond to ping requests from Kali Linux.

### Cause
Windows Defender Firewall blocked inbound ICMP Echo Requests by default.

### Resolution
Enabled:
- File and Printer Sharing (Echo Request - ICMPv4-In)

inside Windows Defender Firewall.

### What Was Learned
- Difference between connectivity issues and firewall filtering
- Importance of firewall rules in enterprise environments
- ICMP troubleshooting techniques

---

# Future Improvements

Planned future enhancements for the lab include:
- Installing Splunk SIEM
- Configuring Sysmon
- Adding Wazuh
- Creating custom detection rules
- Setting up Active Directory
- Simulating brute-force attacks
- Centralized log collection
- Alert monitoring and incident response practice

---

# Conclusion

This project provided practical hands-on experience with:
- Virtualization
- Networking
- Linux and Windows system administration
- Security monitoring
- Troubleshooting
- Basic SOC Analyst workflows

The lab environment serves as a foundation for future cybersecurity projects involving SIEM platforms, endpoint monitoring, detection engineering, and incident response.

---

# Author

Talha Khan

## LinkedIn


## GitHub
INSERT GITHUB PROFILE LINK HERE
