# Project 03 – Active Directory Architecture

## Overview

Project 03 expanded the Windows Server 2022 virtual machine into an enterprise identity infrastructure by deploying Active Directory Domain Services (AD DS), DNS, Organizational Units, Security Groups, and Group Policy.

The environment simulates a small enterprise domain where centralized authentication, authorization, and administration are performed from a single Domain Controller.

---

# Lab Environment

## Host System

- Windows 11
- VMware Workstation Pro

---

## Virtual Machines

### Domain Controller

| Component | Configuration |
|----------|---------------|
| Hostname | SRV-DC01 |
| Operating System | Windows Server 2022 |
| Role | Primary Domain Controller |
| Domain | jamaursec.lab |
| Directory Service | Active Directory Domain Services |
| DNS | Active Directory Integrated DNS |

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
                    VMware Workstation Pro
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

Example policy:

- Restrict Control Panel access

---

# DNS Architecture

DNS provides name resolution for Active Directory.

Configured:

- Forward Lookup Zone
- Active Directory Integrated Zone

Domain:

```
jamaursec.lab
```

---

# Validation Performed

Verified:

- Domain Controller promotion
- DNS functionality
- Active Directory accessibility
- Organizational Unit creation
- User account creation
- Security Group creation
- Group membership
- Password reset
- User disable/enable
- Group Policy processing
- gpresult output

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

---

# Future Expansion

This Active Directory infrastructure serves as the foundation for future Home Lab projects.

Planned integrations include:

- Windows 11 domain-joined client
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