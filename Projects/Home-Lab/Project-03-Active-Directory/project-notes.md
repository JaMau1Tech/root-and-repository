# Project 03 – Active Directory

## Status

✅ Completed

---

# Overview

This project focused on deploying and administering an enterprise Active Directory environment using Windows Server 2022.

The project began with installing the Active Directory Domain Services (AD DS) role and promoting the Windows Server into a Domain Controller. Once the domain was established, enterprise identity management concepts were implemented, including Organizational Units (OUs), user administration, security groups, Group Policy, and Active Directory best practices.

The completed environment simulates the identity infrastructure commonly found in enterprise Windows networks.

---

# Objectives

- Install Active Directory Domain Services (AD DS)
- Configure DNS for Active Directory
- Promote Windows Server to a Domain Controller
- Create a new Active Directory forest
- Configure the `jamaursec.lab` domain
- Create Organizational Units (OUs)
- Create and manage user accounts
- Create and manage security groups
- Implement Group Policy
- Practice enterprise Active Directory administration

---

# Requirements

## Hardware

- Windows 11 Host
- VMware Workstation Pro

## Virtual Machines

- Windows Server 2022

## Software

- Active Directory Domain Services
- DNS Server
- Group Policy Management
- Active Directory Users and Computers
- PowerShell

---

# Installation

## Active Directory Domain Services

- Installed the AD DS server role
- Installed DNS Server
- Installed required management tools

---

## Domain Controller Promotion

- Created a new forest
- Domain Name:

```
jamaursec.lab
```

- Promoted the server to a Domain Controller
- Restarted the server
- Verified Active Directory functionality

---

# Configuration

## DNS

Configured:

- Forward Lookup Zone
- Active Directory integrated DNS
- Domain name resolution

---

## Organizational Units

Created Organizational Units to logically separate administrative objects.

Example:

- IT

---

## User Administration

Created test users.

Example:

- John Doe

Practiced:

- Creating users
- Modifying users
- Password resets
- Account disable/enable
- Account management

---

## Security Groups

Created security groups to manage permissions.

Example:

- IT

Configured:

- User membership
- Group management

---

## Group Policy

Practiced configuring Group Policy Objects.

Verified policy application using:

```powershell
gpresult /R
```

---

# Validation

Verified:

- Domain Controller promotion
- DNS functionality
- Active Directory Users and Computers
- User creation
- Security group membership
- Password reset
- Disabled user account
- Enabled user account
- Group Policy processing
- gpresult output

---

# Commands

## Verify Group Policy

```powershell
gpresult /R
```

---

# Troubleshooting

## Password Administration

Performed:

- Password reset
- User enable
- User disable

Verified successful administration through Active Directory Users and Computers.

---

## Group Membership

Validated:

- Security group creation
- User membership assignment

---

## Domain Services

Verified:

- Active Directory service
- DNS integration
- Domain functionality

---

# Lessons Learned

- Active Directory centralizes identity management.
- DNS is a required component of Active Directory.
- Organizational Units improve administration and Group Policy targeting.
- Security Groups simplify permission management.
- Group Policy centralizes Windows configuration.
- User lifecycle management is a core responsibility of system administrators.
- Documentation and planning are critical for enterprise environments.

---

# Skills Demonstrated

## Windows Server

- Windows Server Administration
- Server Manager
- AD DS Installation

## Active Directory

- Domain Controller Deployment
- Active Directory Users and Computers
- Organizational Units
- User Administration
- Security Groups
- Account Management

## Networking

- DNS
- Active Directory Integration

## Administration

- Password Management
- Account Lifecycle
- Group Membership
- Group Policy
- gpresult Verification

## Professional Skills

- Enterprise Documentation
- Troubleshooting
- Verification
- Change Management
- Identity Management

---

# Project Outcome

Successfully deployed a functional Active Directory environment capable of centralized identity and access management.

The completed infrastructure provides the foundation for future Home Lab projects, including Windows client domain joins, enterprise file services, Group Policy expansion, Help Desk simulations, and enterprise system administration.