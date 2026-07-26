# Project 03 – Active Directory

## Overview

This project focused on deploying and administering an enterprise Active Directory environment using Windows Server 2022.

The project began by installing the Active Directory Domain Services (AD DS) role and promoting the server into a Domain Controller. Once the domain was established, enterprise identity management concepts were implemented through Organizational Units (OUs), user administration, security groups, DNS integration, and Group Policy.

This project represents the foundation of a Windows enterprise infrastructure and provides the identity services required for future Home Lab projects.

---

# Objectives

- Deploy Active Directory Domain Services (AD DS)
- Promote Windows Server to a Domain Controller
- Configure Active Directory Integrated DNS
- Create a new Active Directory forest
- Configure the `jamaursec.lab` domain
- Create Organizational Units (OUs)
- Manage user accounts
- Manage security groups
- Configure and verify Group Policy
- Practice enterprise identity administration

---

# Technologies Used

## Operating System

- Windows Server 2022

## Virtualization

- VMware Workstation Pro

## Windows Roles & Features

- Active Directory Domain Services (AD DS)
- DNS Server
- Group Policy Management

## Administrative Tools

- Server Manager
- Active Directory Users and Computers
- DNS Manager
- Group Policy Management Console
- PowerShell

---

# Skills Demonstrated

## Active Directory

- Active Directory Domain Services
- Domain Controller Deployment
- Forest Creation
- Organizational Unit Design
- User Lifecycle Management
- Security Group Administration
- Group Membership Management
- Identity Management

## Windows Administration

- Windows Server Administration
- Server Roles & Features
- Administrative Tools
- Enterprise Configuration

## Networking

- DNS
- Active Directory Integrated DNS
- Name Resolution

## Group Policy

- Group Policy Management
- Policy Configuration
- gpresult Verification

## Enterprise Concepts

- Centralized Authentication
- Identity & Access Management (IAM)
- Principle of Least Privilege
- Role-Based Administration
- Enterprise Documentation
- Change Management

---

# Project Walkthrough

## 1. Active Directory Installation

- Installed the Active Directory Domain Services role
- Installed DNS Server
- Installed management tools

---

## 2. Domain Controller Promotion

- Created a new forest
- Promoted the server to a Domain Controller
- Verified successful promotion

Domain:

```text
jamaursec.lab
```

---

## 3. DNS Configuration

Configured:

- Active Directory Integrated DNS
- Forward Lookup Zones
- Domain name resolution

---

## 4. Organizational Units

Created Organizational Units to organize Active Directory objects.

Example:

```text
jamaursec.lab
└── IT
```

---

## 5. User Administration

Practiced:

- Creating users
- Managing users
- Password resets
- Disabling accounts
- Enabling accounts

Example user:

- John Doe

---

## 6. Security Groups

Created security groups and assigned users to appropriate groups.

Example:

- IT

---

## 7. Group Policy

Configured and verified Group Policy.

Validation performed using:

```powershell
gpresult /R
```

Example policy:

- Restrict Control Panel access

---

# Screenshots

| Screenshot | Description |
|------------|-------------|
| `project03-active-directory-domain-controller-promoted` | Successful Domain Controller promotion |
| `project03-active-directory-users-and-computers` | Active Directory Users and Computers console |
| `project03-dns-manager-forward-lookup-zones` | DNS configuration |
| `project03-active-directory-first-organizational-unit` | First Organizational Unit |
| `project03-active-directory-first-security-group` | Security Group creation |
| `project03-active-directory-first-user-created` | User account creation |
| `project03-active-directory-user-added-to-security-group` | User assigned to Security Group |
| `project03-active-directory-reset-password-dialog` | Password reset dialog |
| `project03-active-directory-password-reset-complete` | Password reset completed |
| `project03-active-directory-disabled-user-account` | User account disabled |
| `project03-active-directory-enabled-user-account` | User account enabled |
| `project03-active-directory-user-account-administration-complete` | User lifecycle management complete |
| `project-03-domain-controller-computer-properties` | Domain Controller computer properties |
| `project03-group-policy-computer-gpresult` | Computer Group Policy verification |
| `project03-group-policy-user-gpresult` | User Group Policy verification |
| `project03-group-policy-control-panel-policy-enabled` | Group Policy configuration |

---

# Results

Successfully deployed an enterprise Active Directory environment capable of:

- Centralized authentication
- Centralized user management
- Organizational Unit administration
- Security Group administration
- Group Policy management
- Active Directory Integrated DNS
- Enterprise identity management

---

# Lessons Learned

This project reinforced the importance of proper Active Directory planning before deploying enterprise infrastructure.

Key takeaways include:

- DNS is a critical dependency for Active Directory.
- Organizational Units simplify administration and Group Policy targeting.
- Security Groups should manage permissions instead of assigning permissions directly to users.
- Group Policy enables centralized Windows configuration.
- Identity management is the foundation of enterprise Windows environments.
- Documentation and validation are essential administrative practices.

---

# Future Improvements

The Active Directory environment created in this project will support future Home Lab projects, including:

- Windows 11 Domain Join
- DHCP
- Enterprise File Services
- NTFS & Share Permissions
- osTicket Help Desk
- pfSense Firewall
- SIEM Integration
- PowerShell Automation
- Enterprise Troubleshooting

---

# Project Status

**Status:** ✅ Complete

This project establishes the identity infrastructure that future Home Lab projects will build upon.