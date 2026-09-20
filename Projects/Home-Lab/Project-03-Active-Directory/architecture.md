# Project 03 – Active Directory Architecture

## Overview

Project 03 expanded the Windows Server 2022 virtual machine (SRV-DC01, Project 02) into an enterprise identity infrastructure by deploying Active Directory Domain Services (AD DS), DNS, Organizational Units, Security Groups, and Group Policy — on the VirtualBox platform established in Project 01.

The environment simulates a small enterprise domain where centralized authentication, authorization, and administration are performed from a single Domain Controller.

---

# Lab Environment

## Host System

- Ubuntu 26.04.1 LTS
- VirtualBox 7.2.6

---

## Virtual Machines

### Domain Controller

| Component | Configuration |
|----------|---------------|
| Hostname | SRV-DC01 |
| Operating System | Windows Server 2022 |
| Role | Primary Domain Controller |
| Domain | jamaursec.lab |
| NetBIOS Name | JAMAURSEC |
| Domain Functional Level | Windows2016Domain |
| Directory Service | Active Directory Domain Services |
| DNS | Active Directory Integrated DNS |
| IPv4 Address | 192.168.45.129 |

---

# Network Configuration

## Domain

```
jamaursec.lab
```

## Services

- Active Directory Domain Services
- DNS Server
- Group Policy Management
- Active Directory Users and Computers

---

# Logical Architecture

```text
                 VirtualBox 7.2.6 (Ubuntu Host)
                             │
                             │
                    Windows Server 2022
                         SRV-DC01
                             │
          ┌──────────────────┴──────────────────┐
          │                                     │
     Active Directory                     DNS Server
          │                                     │
          ├───────────────┬─────────────────────┤
          │               │                     │
     Organizational     Security            Group
         Units           Groups             Policy
          │               │
          │               │
      User Accounts   Group Membership
```

---

# Active Directory Structure

## Domain

```
jamaursec.lab
```

## Organizational Units

```
jamaursec.lab
└── IT
```

---

## User Objects

Example:

- John Doe

---

## Security Groups

Example:

- IT

---

# Identity Management Workflow

```text
Administrator
        │
        ▼
Active Directory Users and Computers
        │
        ▼
Create User
        │
        ▼
Assign Group Membership
        │
        ▼
Apply Group Policy
        │
        ▼
Authenticate to Domain Resources
```

---

# Group Policy Architecture

Configured and verified:

- Group Policy Management
- Group Policy Objects (GPOs)
- Policy processing
- gpresult validation

Policy deployed:

- **Restrict Control Panel** — linked to the `IT` OU, prohibits access to Control Panel and PC settings for users in that OU

### Verification Constraint

No domain-joined client exists yet (Project 04), so user-scope policy testing was performed by temporarily granting the `IT` group **Allow log on locally** on the domain controller itself, through the Default Domain Controllers Policy. This is a documented lab-only deviation — see project-notes.md — not a production configuration.

---

# DNS Architecture

DNS provides name resolution for Active Directory.

Configured:

- Forward Lookup Zone
- Active Directory Integrated Zone
- The domain controller's own DNS client setting points at itself (192.168.45.129)

Domain:

```
jamaursec.lab
```

---

# Validation Performed

Verified:

- Domain Controller promotion (`whoami`, `Get-ADDomain`)
- DNS functionality
- Active Directory accessibility
- Organizational Unit creation
- User account creation
- Security Group creation
- Group membership
- Password reset
- User disable/enable
- Group Policy processing

---

# Design Decisions

The environment was designed using enterprise administration principles.

Key decisions included:

- Dedicated Domain Controller
- Active Directory Integrated DNS
- Logical Organizational Unit structure
- Security Groups for centralized administration
- Group Policy for centralized configuration
- Identity management through Active Directory

## Platform Differences From the Original Build

This domain previously existed in an earlier iteration of the lab (VMware Workstation Pro), which was lost when that host was reinstalled. The domain name, OU structure, and test objects were rebuilt unchanged; only the underlying hypervisor and host (see Project 01 and Project 02) differ.

---

# Future Expansion

This Active Directory infrastructure serves as the foundation for future Home Lab projects.

Planned integrations include:

- Windows 11 domain-joined client (removes the need for the lab-only DC local-logon deviation)
- Enterprise File Services
- NTFS & Share Permissions
- DHCP
- osTicket Help Desk
- pfSense Firewall
- SIEM
- PowerShell automation
- Enterprise troubleshooting scenarios

---

# Skills Demonstrated

- Windows Server Administration
- Active Directory Domain Services
- Domain Controller Deployment
- DNS Administration
- Organizational Unit Design
- User Administration
- Security Group Management
- Group Policy Management
- Identity & Access Management
- Enterprise Infrastructure Design
