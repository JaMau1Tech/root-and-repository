# Home Lab

## Overview

This repository documents the development of a hands-on enterprise Home Lab built to strengthen practical IT and cybersecurity skills through real-world infrastructure projects.

The environment is hosted in VMware Workstation Pro and simulates a small enterprise network. Each project builds upon the previous one, progressing from virtualization and operating system deployment into enterprise identity management, Windows administration, networking, security, and IT operations.

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

- Windows 11
- VMware Workstation Pro

## Virtual Machines

| Virtual Machine | Status | Purpose |
|-----------------|:------:|---------|
| Ubuntu 24.04 LTS | ✅ Complete | Linux administration and virtualization foundation |
| Windows Server 2022 | ✅ Complete | Enterprise infrastructure server |
| Windows 11 Client | ⏳ Next Project | Domain-joined workstation |
| pfSense Firewall | ⏳ Planned | Firewall, routing, and network segmentation |
| Additional Security Systems | ⏳ Planned | Future security and monitoring projects |

---

# Completed Projects

## ✅ Project 01 – Ubuntu Foundation

### Skills Developed

- VMware Workstation
- Ubuntu Server
- Linux CLI
- Package Management
- SSH
- System Administration

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

# Project Roadmap

| Project | Status |
|---------|:------:|
| Project 01 – Ubuntu Foundation | ✅ Complete |
| Project 02 – Windows Server Foundation | ✅ Complete |
| Project 03 – Active Directory | ✅ Complete |
| Project 04 – Windows 11 Client | ⏳ Next |
| Project 05 – File Services | ⏳ Planned |
| Project 06 – Security Hardening | ⏳ Planned |
| Project 07 – Monitoring & Logging | ⏳ Planned |
| Project 08 – osTicket Help Desk | ⏳ Planned |
| Project 09 – pfSense Firewall | ⏳ Planned |
| Project 10 – SIEM | ⏳ Planned |

---

# Current Lab Architecture

```text
                    VMware Workstation Pro
                             │
         ┌───────────────────┴───────────────────┐
         │                                       │
  Ubuntu 24.04                          Windows Server 2022
   Project 01                                SRV-DC01
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
          Windows 11 Client (Next)
```

---

# Skills Gained

## Virtualization

- VMware Workstation Pro
- Virtual Machine Deployment
- Virtual Hardware Configuration
- Snapshot Management

## Linux

- Ubuntu Administration
- Linux Command Line
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
- NAT Networking

---

# Repository Structure

```text
Home-Lab/
├── README.md
├── Project-01-Ubuntu-Foundation/
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
| Projects Completed | **3 / 10** |
| Current Project | **Project 04 – Windows 11 Client** |
| Infrastructure Status | **Enterprise Active Directory Operational** |

---

# Next Project

## Project 04 – Windows 11 Client

### Objectives

- Install Windows 11
- Configure networking
- Join the `jamaursec.lab` domain
- Verify domain authentication
- Apply Group Policy
- Test centralized administration
- Validate communication with the Domain Controller

---

# Future Projects

Following the Windows 11 domain join, the Home Lab will continue expanding into enterprise administration with:

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

**J Wi**

Enterprise Home Lab Portfolio