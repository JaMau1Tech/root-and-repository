# Home Lab

## Overview

This repository documents the development of a hands-on enterprise Home Lab built to strengthen practical IT and cybersecurity skills through real-world infrastructure projects.

The environment is hosted on a dedicated Ubuntu LTS machine running VirtualBox, and simulates a small enterprise network. Each project builds upon the previous one, progressing from virtualization and operating system deployment into enterprise identity management, Windows administration, networking, security, and IT operations.

The lab was rebuilt on this platform after its original host (Windows 11 Home, VMware Workstation Pro) was reinstalled. The domain, server roles, and project objectives are unchanged from the original build; the underlying host and hypervisor are not. See each project's `project-notes.md` for platform-specific details.

---

# Objectives

- Develop practical system administration skills
- Build enterprise Windows infrastructure
- Practice Linux administration
- Gain experience with virtualization
- Configure enterprise networking
- Deploy Active Directory Domain Services
- Implement centralized identity and access management
- Prepare for IT Support, System Administration, and Cybersecurity roles

---

# Lab Environment

## Host Platform

- Dell Latitude 5320 (Intel Core i5-1145G7, 16 GB RAM, 512 GB disk)
- Ubuntu 26.04.1 LTS
- VirtualBox 7.2.6

## Virtual Machines

| Virtual Machine | Status | Purpose |
|-----------------|:------:|---------|
| Ubuntu 26.04.1 LTS (host) | ✅ Complete | Hypervisor host and Linux administration foundation — not a guest VM |
| Windows Server 2022 (SRV-DC01) | ✅ Complete | Enterprise infrastructure server / Domain Controller |
| Windows 11 Client (WKS-W11-01) | ✅ Complete | Domain-joined workstation |
| pfSense Firewall | ⏳ Planned | Firewall, routing, and network segmentation |
| Additional Security Systems | ⏳ Planned | Future security and monitoring projects |

---

# Completed Projects

## ✅ Project 01 – Virtualization Foundation

### Skills Developed

- Ubuntu LTS installation and hardening
- Firewall, disk encryption, automatic updates, Secure Boot
- VirtualBox installation and Secure Boot module signing (MOK enrollment)
- Virtual networking (NAT Network design)

---

## ✅ Project 02 – Windows Server Foundation

### Skills Developed

- Windows Server Installation
- Static Networking
- Windows Updates
- Server Manager
- PowerShell
- Snapshot Management

---

## ✅ Project 03 – Active Directory

### Objectives

- Deploy Active Directory Domain Services
- Promote a Domain Controller
- Configure Active Directory Integrated DNS
- Create Organizational Units
- Create and manage users
- Create and manage security groups
- Configure Group Policy
- Practice enterprise identity management

### Skills Developed

- Active Directory Domain Services
- Domain Controller Deployment
- DNS Administration
- Organizational Unit Design
- User Lifecycle Management
- Security Group Administration
- Group Membership Management
- Password Administration
- Account Enable / Disable
- Group Policy Management
- gpresult Verification
- Enterprise Identity Management

---

## ✅ Project 04 – Windows 11 Client

### Objectives

- Deploy a Windows 11 Enterprise Evaluation client
- Configure EFI, TPM 2.0, and Secure Boot
- Configure static DNS
- Join the client to the `jamaursec.lab` domain
- Verify domain authentication
- Verify Group Policy from a real domain-joined client
- Confirm the client's computer object in Active Directory
- Retire the Project 03 DC local-logon lab deviation

### Skills Developed

- Windows 11 Client Deployment
- EFI / TPM 2.0 / Secure Boot Configuration
- Static DNS Configuration
- Domain Join Administration
- Computer Rename Workflows
- Group Policy Verification (Client-Side)
- Active Directory Computer Object Administration
- Security Posture Restoration

---

# Project Roadmap

| Project | Status |
|---------|:------:|
| Project 01 – Virtualization Foundation | ✅ Complete |
| Project 02 – Windows Server Foundation | ✅ Complete |
| Project 03 – Active Directory | ✅ Complete |
| Project 04 – Windows 11 Client | ✅ Complete |
| Project 05 – File Services | ⏳ Next |
| Project 06 – Security Hardening | ⏳ Planned |
| Project 07 – Monitoring & Logging | ⏳ Planned |
| Project 08 – osTicket Help Desk | ⏳ Planned |
| Project 09 – pfSense Firewall | ⏳ Planned |
| Project 10 – SIEM | ⏳ Planned |

---

# Current Lab Architecture

```text
                    Ubuntu 26.04.1 LTS Host
                     (Dell Latitude 5320)
                             │
                     VirtualBox 7.2.6
                             │
                  NAT Network: jamaursec-nat
                             │
                    Windows Server 2022
                         SRV-DC01
                             │
                   Active Directory
                      jamaursec.lab
                             │
        ┌──────────────┬──────────────┬──────────────┐
        │              │              │
       DNS            OUs        Security Groups
        │
 Group Policy
        │
Windows 11 Client (WKS-W11-01)
        │
 Domain-Joined, Policy Verified
```

---

# Skills Gained

## Virtualization

- VirtualBox
- Virtual Machine Deployment
- Virtual Hardware Configuration
- Secure Boot Module Signing (MOK)
- Snapshot Management

## Linux

- Ubuntu Administration
- Linux Command Line
- System Hardening (firewall, disk encryption, automatic updates)
- Package Management
- System Configuration

## Windows

- Windows Server Administration
- Server Manager
- PowerShell
- Enterprise Configuration

## Active Directory

- Active Directory Domain Services
- Domain Controller Deployment
- Organizational Units
- User Administration
- Security Groups
- Identity Management
- Group Policy

## Networking

- IPv4 Configuration
- DNS
- Active Directory Integrated DNS
- NAT Network Design

---

# Repository Structure

```text
Home-Lab/
├── README.md
├── Project-01-Virtualization-Foundation/
├── Project-02-Windows-Server/
├── Project-03-Active-Directory/
├── Project-04-Windows-11-Client/
├── Project-05-File-Services/
├── Project-06-Security-Hardening/
├── Project-07-Monitoring-Logging/
├── Project-08-osTicket/
├── Project-09-pfSense/
└── Project-10-SIEM/
```

---

# Progress

| Metric | Status |
|--------|--------|
| Projects Completed | **4 / 10** |
| Current Project | **Project 05 – File Services** |
| Infrastructure Status | **Enterprise Active Directory Operational, Domain-Joined Client Verified** |

---

# Next Project

## Project 05 – File Services

### Objectives

- Deploy enterprise file shares on `SRV-DC01`
- Configure NTFS and share-level permissions
- Apply permissions through the `IT` security group
- Map network drives from `WKS-W11-01`
- Validate access control from the domain-joined client

Project 04 closed the loop between Active Directory's policy layer and a real client, retiring the Project 03 lab-only DC local-logon deviation. Project 05 builds on that same client to validate file-level access control the same way — from a genuine domain-joined machine rather than the server console.

---

# Future Projects

With a domain-joined client now validating Active Directory end-to-end, the Home Lab will continue expanding into enterprise administration with:

- Enterprise File Services
- NTFS & Share Permissions
- DHCP
- osTicket Help Desk
- pfSense Firewall
- SIEM Integration
- PowerShell Automation
- Enterprise Troubleshooting Scenarios

---

# Author

**Ja'Maurian Williams**

Enterprise Home Lab Portfolio
