# Architecture – Project 02: Windows Server Foundation

## Overview

This document describes the architecture, configuration, and purpose of the Windows Server virtual machine built during Project 02, on the VirtualBox platform established in Project 01.

The server serves as the enterprise infrastructure foundation for the Home Lab and will later be promoted to an Active Directory Domain Controller.

---

# Architecture Summary

## Hypervisor

VirtualBox 7.2.6

## Host Operating System

Ubuntu 26.04.1 LTS

## Guest Operating System

Windows Server 2022 Standard Evaluation (Desktop Experience)

---

# Virtual Machine Specifications

| Component | Configuration |
|-----------|---------------|
| VM Name | Windows Server 2022 |
| Hostname | SRV-DC01 |
| Computer Description | Primary Domain Controller |
| Firmware | EFI (enabled) |
| Memory | 4096 MB |
| CPU | 2 vCPUs |
| Disk Size | 60 GB |
| Disk Controller | SATA |
| Network Adapter | Intel PRO/1000 MT Desktop, NAT Network `jamaursec-nat` |
| Guest Additions | Installed (7.2.6) |
| Snapshot | Windows Server Baseline |

---

# Network Configuration

## IPv4 Configuration

| Setting | Value |
|---------|-------|
| IP Address | 192.168.45.129 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.45.1 |
| Network Type | VirtualBox NAT Network (`jamaursec-nat`) |

---

# Network Layout

```text
                Internet
                    │
                    │
         Ubuntu 26.04.1 LTS Host
              (Dell Latitude 5320)
                    │
            VirtualBox 7.2.6
                    │
        NAT Network: jamaursec-nat
           192.168.45.0/24
           Gateway: 192.168.45.1
                    │
          ┌──────────────────┐
          │                  │
          │    SRV-DC01      │
          │ Windows Server   │
          │ 192.168.45.129   │
          │                  │
          └──────────────────┘
```

---

# Server Purpose

Current Responsibilities

- Windows Server installation
- Enterprise server baseline
- Virtual infrastructure foundation

Future Responsibilities

- Active Directory Domain Services
- DNS Server
- Authentication
- Group Policy
- Domain Controller
- User Management
- Computer Management

---

# Software Installed

## Operating System

- Windows Server 2022 Standard Evaluation

## Virtualization Components

- VirtualBox Guest Additions 7.2.6

## Windows Components

- Server Manager
- Windows PowerShell
- Windows Update

---

# Security Baseline

Completed

- Windows fully updated
- VirtualBox Guest Additions installed
- Enterprise hostname configured
- Static IPv4 address assigned
- Baseline snapshot created

Future Configuration

- Active Directory
- DNS
- DHCP (optional)
- Group Policy
- Organizational Units
- Security Groups
- User Accounts

---

# Verification Performed

## Operating System

- Successful installation (Desktop Experience, selected manually — see project-notes.md)
- Successful login
- GUI verified

## Network

- Static IP verified
- Gateway verified
- Internet connectivity verified
- DNS resolution verified

## Virtual Machine

- Guest Additions verified
- Snapshot created
- Stable boot confirmed

---

# Recovery

## VirtualBox Snapshot

Snapshot Name

Windows Server Baseline

Purpose

Provides a rollback point before deploying enterprise infrastructure services.

---

# Platform Differences From the Original Build

This server previously existed in an earlier iteration of the lab (VMware Workstation Pro, Windows 11 host), which was lost when that host was reinstalled. The rebuild targets the same role, hostname, and IP — the platform underneath it changed:

| Item | Original | Current |
|---|---|---|
| Hypervisor | VMware Workstation Pro | VirtualBox 7.2.6 |
| Host OS | Windows 11 | Ubuntu 26.04.1 LTS |
| Disk controller | SCSI | SATA |
| Guest integration | VMware Tools | VirtualBox Guest Additions |
| Network | VMware NAT | VirtualBox NAT Network (`jamaursec-nat`) |
| Default gateway | 192.168.45.2 | 192.168.45.1 |

Hostname (`SRV-DC01`), description, static IP (`192.168.45.129`), memory (4 GB), CPU count (2), and disk size (60 GB) are unchanged.

---

# Project Dependencies

## Previous Project

Project 01

Virtualization Foundation

Purpose

Hardened Ubuntu host, VirtualBox hypervisor, and lab NAT Network.

---

## Next Project

Project 03

Active Directory

Objectives

- Install AD DS
- Install DNS
- Promote SRV-DC01
- Create Forest
- Create Domain
- Verify Authentication
- Join Windows 11 Client

---

# Overall Home Lab Architecture

```text
                          Home Lab

                  Ubuntu 26.04.1 LTS Host
                    (Dell Latitude 5320)
                             │
                     VirtualBox 7.2.6
                             │
                  NAT Network: jamaursec-nat
                             │
                       Windows Server
                         Project 02
                             │
                             │
                   Active Directory
                         Project 03
                             │
             ┌──────────────┴──────────────┐
             │                             │
        Domain Users                 Domain Computers
                             │
                       Windows 11
                        Project 04

                 Future Infrastructure

        pfSense Firewall
        SIEM Platform
        Security Monitoring
```

---

# Architecture Summary

This Windows Server virtual machine serves as the core infrastructure server for the Home Lab, now rebuilt on VirtualBox after the platform migration in Project 01.

All future Windows-based enterprise services—including Active Directory, DNS, authentication, Group Policy, and domain management—will be deployed from this system.

The baseline snapshot provides a stable recovery point before introducing additional server roles.
