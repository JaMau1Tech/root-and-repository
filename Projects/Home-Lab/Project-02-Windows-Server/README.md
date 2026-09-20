# Project 02 – Windows Server Foundation

## Overview

Project 02 deploys and configures the Windows Server 2022 virtual machine that serves as the core infrastructure server for the Home Lab, built on the VirtualBox platform established in Project 01.

The server was manually installed in VirtualBox, configured using enterprise best practices, updated, integrated with VirtualBox Guest Additions, assigned a static IP address, and prepared for Active Directory deployment.

This is a rebuild of the same server role from an earlier iteration of the lab (VMware Workstation Pro on a Windows 11 host), which was lost when that host was reinstalled. See `project-notes.md` for the platform differences.

---

## Objectives

- Deploy Windows Server 2022 in VirtualBox
- Configure enterprise virtual hardware
- Install Windows Server manually
- Configure a static IP address
- Install VirtualBox Guest Additions
- Apply Windows Updates
- Configure enterprise hostname
- Create a VirtualBox baseline snapshot
- Prepare for Active Directory

---

## Technologies Used

### Virtualization

- VirtualBox 7.2.6

### Operating System

- Windows Server 2022 Standard Evaluation
- Desktop Experience (GUI)

### Networking

- IPv4
- VirtualBox NAT Network (`jamaursec-nat`)
- Static IP Configuration

### Administration

- Windows Server Manager
- Windows PowerShell
- Windows Update

---

## Virtual Machine Configuration

| Component | Configuration |
|-----------|---------------|
| Hypervisor | VirtualBox 7.2.6 |
| Firmware | EFI (enabled) |
| Memory | 4096 MB |
| CPU | 2 vCPUs |
| Disk | 60 GB |
| Disk Controller | SATA |
| Network | NAT Network — `jamaursec-nat` |
| Guest Additions | Installed |

---

## Server Configuration

| Setting | Value |
|---------|-------|
| Hostname | SRV-DC01 |
| Description | Primary Domain Controller |
| IPv4 Address | 192.168.45.129 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.45.1 |

---

## Project Workflow

- Create virtual machine (Skip Unattended Installation)
- Install Windows Server (Desktop Experience)
- Configure enterprise settings
- Install VirtualBox Guest Additions
- Apply Windows Updates
- Configure static networking
- Verify connectivity
- Create baseline snapshot

---

## Skills Developed

### Windows Server

- Windows Server installation and edition selection
- Server Manager administration
- Windows Updates
- Enterprise configuration

### Virtualization

- VirtualBox virtual machine deployment
- Guest Additions installation
- Snapshot management

### Networking

- IPv4 configuration
- Static addressing
- Network verification
- Internet connectivity testing

### PowerShell

- Hostname verification
- Network verification
- Connectivity testing

---

## Screenshots

| Screenshot | Description |
|------------|-------------|
| project-02-windows-server-vm-created | Virtual machine created |
| project-02-windows-server-installation | Server Manager > Local Server, confirming Desktop Experience |
| project-02-windows-server-first-login | First successful login |
| project-02-windows-server-server-manager | Server Manager dashboard |
| project-02-windows-server-terminal-verification | PowerShell verification |
| project-02-windows-server-renamed | Enterprise hostname configured |
| project-02-vmware-tools-installed | VirtualBox Guest Additions installation |
| project-02-windows-server-static-ip | Static IP configuration |
| project-02-windows-server-baseline-snapshot | VirtualBox baseline snapshot |

---

## Challenges Encountered

### Server Core Highlighted by Default

The Windows Server setup wizard highlights the no-GUI "Standard Evaluation" (Server Core) option by default.

**Resolution**

Manually selected "Windows Server 2022 Standard Evaluation (Desktop Experience)" before proceeding with installation.

---

### Static IP Typo

The static IP was initially entered as 195.168.45.129 instead of the intended 192.168.45.129.

**Resolution**

Corrected the address and re-verified with `ipconfig` and `ping google.com`.

---

## Lessons Learned

- Deliberately skipping the unattended-install wizard avoids the licensing failures the previous hypervisor's quick-install path produced.
- A successful `ping` doesn't confirm a static IP was typed correctly — verify the actual `ipconfig` output.
- Enterprise naming conventions improve server administration.
- VirtualBox Guest Additions should be installed immediately after OS installation.
- Baseline snapshots simplify recovery and future experimentation.

---

## Project Outcome

Successfully deployed and configured a production-style Windows Server virtual machine on VirtualBox.

Completed tasks include:

- Windows Server installation
- Enterprise hostname configuration
- Static IP configuration
- VirtualBox Guest Additions installation
- Windows Updates
- Network verification
- Baseline VirtualBox snapshot

The server is now fully prepared for Active Directory deployment.

---

## Project Structure

```text
Project-02-Windows-Server/
├── README.md
├── architecture.md
├── project-notes.md
└── images/
    ├── project-02-windows-server-vm-created.png
    ├── project-02-windows-server-installation.png
    ├── project-02-windows-server-first-login.png
    ├── project-02-windows-server-server-manager.png
    ├── project-02-windows-server-terminal-verification.png
    ├── project-02-windows-server-renamed.png
    ├── project-02-vmware-tools-installed.png
    ├── project-02-windows-server-static-ip.png
    └── project-02-windows-server-baseline-snapshot.png
```

---

## Next Project

### Project 03 – Active Directory

Upcoming objectives:

- Install Active Directory Domain Services (AD DS)
- Install DNS Server
- Promote **SRV-DC01** to a Domain Controller
- Create a new Active Directory forest
- Configure the lab domain
- Create Organizational Units (OUs)
- Create users and groups
- Join a Windows 11 client to the domain

---

## Author

**Ja'Maurian Williams**

Home Lab Series

Project 02 – Windows Server Foundation
