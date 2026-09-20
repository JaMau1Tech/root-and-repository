# Project 02 – Windows Server Foundation

## Status

✅ Completed

---

# Overview

This project focused on building the Windows Server foundation for the Home Lab on VirtualBox, the hypervisor established in Project 01. A Windows Server 2022 virtual machine was deployed, configured using enterprise best practices, updated, integrated with VirtualBox Guest Additions, assigned a static IP address, and prepared as the future Active Directory Domain Controller.

This is a rebuild of the same server that existed in the lab's earlier VMware-based iteration, which was lost when that host was reinstalled. The target configuration (hostname, IP, role) is unchanged; the hypervisor and a handful of platform-specific details are not.

---

# Objectives

- Deploy Windows Server 2022 in VirtualBox
- Configure enterprise virtual hardware
- Perform a manual operating system installation
- Configure enterprise server settings
- Install VirtualBox Guest Additions
- Apply Windows Updates
- Configure a static IP address
- Create a VirtualBox recovery snapshot
- Prepare the server for Active Directory

---

# Environment

## Host System

- Ubuntu 26.04.1 LTS
- VirtualBox 7.2.6
- (See [[Project 01 – Virtualization Foundation]])

## Guest Operating System

- Windows Server 2022 Standard Evaluation
- Desktop Experience (GUI)

---

# Virtual Machine Configuration

| Component | Configuration |
|-----------|---------------|
| Hypervisor | VirtualBox 7.2.6 |
| Firmware | EFI (enabled) |
| Memory | 4096 MB |
| Processors | 2 vCPUs |
| Hard Disk | 60 GB |
| Disk Controller | SATA |
| Network | NAT Network — `jamaursec-nat` |
| Network Adapter | Intel PRO/1000 MT Desktop |
| Guest Additions | Installed (7.2.6) |

---

# Installation Process

## VM Creation

The virtual machine was created with **Skip Unattended Installation** enabled. The lab's earlier VMware build had failed when using its equivalent quick-install path (VMware Easy Install produced licensing errors), so the unattended path was skipped from the start here rather than troubleshooted after a failure.

### Configuration

- EFI firmware
- SATA virtual disk
- 60 GB virtual disk (dynamically allocated)
- 4096 MB RAM
- 2 vCPUs
- NAT Network (`jamaursec-nat`)

---

## Operating System Installation

Windows Server 2022 Standard Evaluation (Desktop Experience) was installed using the ISO image.

**Note:** the setup wizard's edition list highlights **Windows Server 2022 Standard Evaluation** (Server Core, no GUI) by default. Desktop Experience has to be selected manually — it's easy to click Next past it. This was caught before installing.

The Desktop Experience edition was selected to provide a graphical user interface suitable for learning Windows Server administration.

---

# Initial Server Configuration

## Server Name

Hostname:

SRV-DC01

Computer Description:

Primary Domain Controller

The server naming convention follows enterprise standards and prepares the system for future Active Directory deployment.

---

## Windows Updates

Performed:

- Windows Update
- Installed available updates
- Restarted server
- Verified successful installation

---

## VirtualBox Guest Additions

VirtualBox Guest Additions 7.2.6 was installed successfully via the Guest Additions CD image (`VBoxWindowsAdditions.exe`).

Benefits:

- Improved graphics performance
- Enhanced mouse integration
- Better display resizing
- Time synchronization
- Optimized virtual hardware drivers
- Graceful shutdown support

---

# Network Configuration

## Static IPv4 Configuration

| Setting | Value |
|---------|-------|
| IPv4 Address | 192.168.45.129 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.45.1 |
| DNS (temporary) | 8.8.8.8 |

Internet connectivity was verified after assigning the static IP address. DNS is repointed to the server itself (192.168.45.129) once Active Directory DNS is installed in Project 03.

---

# Verification

The following commands were executed to validate the installation.

```powershell
hostname
```

Verified:

- Hostname changed successfully (SRV-DC01)

---

```powershell
whoami
```

Verified:

- Administrator account (srv-dc01\administrator)

---

```powershell
ipconfig
```

Verified:

- Static IP configuration (192.168.45.129)
- Gateway (192.168.45.1)
- Subnet mask (255.255.255.0)

---

```powershell
ping google.com
```

Verified:

- Internet connectivity
- DNS resolution
- 0% packet loss

---

# VirtualBox Snapshot

Snapshot Name:

Windows Server Baseline

Purpose:

Provides a recovery point after completing the initial server configuration and before installing Active Directory.

---

# Challenges Encountered

## Server Core Highlighted by Default

Issue:

The Windows Server setup wizard's edition picker highlights the no-GUI "Standard Evaluation" (Server Core) option by default.

Resolution:

Manually selected "Windows Server 2022 Standard Evaluation (Desktop Experience)" before proceeding.

---

## Static IP Typo

Issue:

The static IP was initially entered as 195.168.45.129 instead of 192.168.45.129. `ping google.com` still succeeded despite the incorrect subnet, which could have masked the error.

Resolution:

Corrected the address to 192.168.45.129 and re-verified with `ipconfig` and `ping` before proceeding.

---

## Lessons Learned

- Manual, deliberate installation choices (skip unattended install, verify the edition before proceeding) avoid repeating the licensing failure hit on the previous hypervisor.
- A successful `ping` does not confirm a static IP was typed correctly — always re-check the actual `ipconfig` output against the intended value.
- VirtualBox's NAT Network gateway defaults to `.1`, not the `.2` used by the previous VMware NAT network — worth confirming per-platform rather than assuming.
- Guest Additions should be installed immediately after OS installation, before further configuration.
- Creating a recovery snapshot before major changes (Active Directory) simplifies troubleshooting.

---

# Skills Developed

## Virtualization

- VirtualBox VM creation
- Guest Additions installation
- Snapshot management

## Windows Server

- Windows Server installation and edition selection
- Server Manager
- Windows administration

## Networking

- IPv4 configuration
- Static addressing
- Connectivity testing

## System Administration

- Windows Update
- PowerShell verification

---

# Project Outcome

Successfully deployed and configured a Windows Server 2022 virtual machine on VirtualBox using enterprise best practices.

The server now serves as the foundation for future Home Lab projects including:

- Active Directory Domain Services
- DNS
- DHCP
- Group Policy
- Windows 11 domain joining
- Enterprise user and computer management

---

# Next Project

Project 03 – Active Directory

Objectives:

- Install Active Directory Domain Services
- Install DNS Server
- Promote SRV-DC01 to a Domain Controller
- Create a new forest
- Create the lab domain
- Verify Active Directory functionality
