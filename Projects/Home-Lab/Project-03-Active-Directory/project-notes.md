# Project 03 – Active Directory

## Status

✅ Completed

---

# Overview

This project focused on deploying and administering an enterprise Active Directory environment on SRV-DC01, the Windows Server 2022 VM rebuilt in Project 02 on VirtualBox.

The project began with installing the Active Directory Domain Services (AD DS) role and promoting the server into a Domain Controller. Once the domain was established, enterprise identity management concepts were implemented: Organizational Units (OUs), user administration, security groups, DNS integration, and Group Policy.

This is a rebuild of the same domain from an earlier iteration of the lab (VMware Workstation Pro), which was lost when that host was reinstalled. The domain name, OU structure, and test accounts are unchanged; the underlying hypervisor and host are not.

---

# Objectives

- Install Active Directory Domain Services (AD DS)
- Configure DNS for Active Directory
- Promote SRV-DC01 to a Domain Controller
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

- Dell Latitude 5320 host

## Hypervisor

- VirtualBox 7.2.6 (see [[Project 01 – Virtualization Foundation]])

## Virtual Machines

- SRV-DC01 — Windows Server 2022 (see [[Project 02 – Windows Server Foundation]])

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

- NetBIOS name: `JAMAURSEC`
- Domain/forest functional level: Windows2016Domain (default for a Windows Server 2022 forest)
- DSRM password set during promotion and recorded outside the repository (never documented here)
- Promoted the server to a Domain Controller
- Restarted the server
- Verified Active Directory functionality

Post-promotion verification (PowerShell):

```powershell
whoami
Get-ADDomain | Select-Object DNSRoot, NetBIOSName, DomainMode
```

Result:

```
jamaursec\administrator

DNSRoot         NetBIOSName    DomainMode
-------         -----------    ----------
jamaursec.lab   JAMAURSEC      Windows2016Domain
```

---

# Configuration

## DNS

Configured:

- Forward Lookup Zone
- Active Directory integrated DNS
- Domain name resolution
- SRV-DC01's own Preferred DNS server repointed from a temporary public resolver to itself (192.168.45.129), so the domain controller resolves the domain through itself rather than an external server

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

Created a Group Policy Object named **Restrict Control Panel**, linked to the `IT` OU, with **Prohibit access to Control Panel and PC settings** set to Enabled under User Configuration > Administrative Templates > Control Panel.

Verified policy application using:

```powershell
gpupdate /force
gpresult /R /SCOPE COMPUTER
gpresult /R /SCOPE USER
```

### Lab-Only Deviation: DC Local Logon

By default, domain users cannot log on locally to a domain controller, which blocked testing the user-scope Group Policy result directly on SRV-DC01 (no domain-joined client exists yet — that's Project 04). To test it, the `IT` group was temporarily granted **Allow log on locally** on SRV-DC01 through the Default Domain Controllers Policy (Computer Configuration > Windows Settings > Security Settings > Local Policies > User Rights Assignment).

This is a lab-only shortcut and is not a production practice — domain controllers should not have their local-logon rights extended to ordinary domain users. It exists here solely to verify Group Policy processing before Project 04 provides a proper domain-joined client to test against.

---

# Validation

Verified:

- Domain Controller promotion (`whoami`, `Get-ADDomain`)
- DNS functionality
- Active Directory Users and Computers
- User creation
- Security group membership
- Password reset
- Disabled user account
- Enabled user account
- Group Policy processing (John Doe successfully logged on after the temporary local-logon grant)

---

# Commands

## Verify Domain Controller Promotion

```powershell
whoami
Get-ADDomain | Select-Object DNSRoot, NetBIOSName, DomainMode
Get-ADDomainController | Select-Object Name, Domain, IPv4Address
```

## Verify DNS

```powershell
nslookup jamaursec.lab
```

## Verify Core Services

```powershell
Get-Service NTDS, DNS, Netlogon
```

## Verify Group Policy

```powershell
gpupdate /force
gpresult /R /SCOPE COMPUTER
gpresult /R /SCOPE USER
```

---

# Troubleshooting

## Domain User Blocked From Logging On to the DC

Issue:

John Doe's first sign-in attempt on SRV-DC01 failed with "The sign-in method you're trying to use isn't allowed." Domain users cannot log on locally to a domain controller by default.

Investigation:

Confirmed John Doe's group membership in Active Directory Users and Computers, then checked the Default Domain Controllers Policy's **Allow log on locally** user right, which did not include the `IT` group.

Resolution:

Added the `IT` group to **Allow log on locally** in the Default Domain Controllers Policy, ran `gpupdate /force`, and confirmed John Doe could then sign in. Documented as a lab-only deviation above.

---

## Command Continuation Swallowing Output

Issue:

Running `Get-ADDomainController | Select-Object ...` immediately after another multi-line paste caused PowerShell to treat it as a line continuation (`>>`), and no output was returned.

Resolution:

Re-ran the command on its own line.

---

# Lessons Learned

- Active Directory centralizes identity management.
- DNS is a required component of Active Directory, and a domain controller's own DNS setting must point at itself (or another domain DNS server) after promotion — not an external resolver.
- Organizational Units improve administration and Group Policy targeting.
- Security Groups simplify permission management.
- Domain controllers block local logon for ordinary domain users by default — a real and useful security boundary, but one that has to be temporarily relaxed to test user-scope Group Policy without a domain-joined client available yet.
- Pasting multiple PowerShell commands together can cause line-continuation issues — run verification commands individually when in doubt.
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

Successfully rebuilt a functional Active Directory environment on the VirtualBox platform, capable of centralized identity and access management.

The completed infrastructure provides the foundation for future Home Lab projects, including Windows client domain joins, enterprise file services, Group Policy expansion, Help Desk simulations, and enterprise system administration.
