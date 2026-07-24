# Active Directory Hardening

## Status

✅ Completed

---

## Room Information

| Item | Details |
|------|---------|
| Platform | TryHackMe |
| Collection | Active Directory |
| Room | Active Directory Hardening |
| Difficulty | Easy |
| Status | Completed |
| Completion Date | 2026-07-23 |

---

# Overview

This room introduced the fundamental concepts of Active Directory hardening and Microsoft's recommended security practices for securing Windows enterprise environments. Topics included authentication hardening, implementing the Principle of Least Privilege, Microsoft's Security Compliance Toolkit, password policies, Group Policy security settings, and defending against common Active Directory attacks.

The room also provided practical experience configuring security policies through the Group Policy Management Editor and reviewing Microsoft's security baseline scripts.

---

# Objectives

- Understand Active Directory hardening concepts
- Configure authentication security policies
- Disable legacy authentication mechanisms
- Enable secure network communications
- Implement Least Privilege principles
- Learn Microsoft's Security Compliance Toolkit
- Understand common Active Directory attack vectors
- Review enterprise password policies

---

# Tasks Completed

## Task 1 – Introduction

### Topics Covered

- Active Directory hardening overview
- Defense-in-depth
- Continuous security improvement

### Skills Learned

- Understanding enterprise hardening
- Security lifecycle concepts

---

## Task 2 – Understanding Active Directory Concepts

### Topics Covered

- Domains
- Domain Controllers
- Trees
- Forests
- Trust Relationships
- Containers
- Leaf Objects

### Key Finding

Root Domain

```text
tryhackme.loc
```

### Skills Learned

- Active Directory architecture
- Enterprise directory hierarchy
- Authentication boundaries

---

## Task 3 – Securing Authentication Methods

### Configurations Reviewed

- Disabled LAN Manager (LM) Hash Storage
- Enabled SMB Signing
- Required LDAP Signing
- Reviewed Password Policy
- Password Rotation Concepts

### Password Policy

| Setting | Value |
|---------|------|
| Minimum Password Length | 7 Characters |

### Skills Learned

- Authentication hardening
- Group Policy configuration
- Password security
- Secure authentication protocols

---

## Task 4 – Least Privilege Model

### Topics Covered

- Principle of Least Privilege
- Role-Based Access Control (RBAC)
- Tiered Administration Model
- Account auditing
- Administrative account separation

### Tier Model

**Tier 0**

- Domain Controllers
- Domain Admins
- Enterprise Admins

**Tier 1**

- Member Servers
- Applications

**Tier 2**

- User Workstations

### Skills Learned

- Privilege management
- Administrative separation
- Enterprise access control

---

## Task 5 – Microsoft Security Compliance Toolkit

### Topics Covered

- Microsoft Security Baselines
- Policy Analyzer
- Security Baseline deployment
- Group Policy comparison

### Practical Activities

Reviewed:

- BaselineLocalInstall.ps1
- Merge-PolicyRules.ps1

### Skills Learned

- Microsoft Security Compliance Toolkit
- Policy Analyzer
- Enterprise security baselines

---

## Task 6 – Protecting Against Known Attacks

### Topics Covered

- Kerberoasting
- Weak Passwords
- Password Auditing
- Brute Force Protection
- Public SMB Shares

### Practical Activities

- Reviewed password audit report
- Examined password reuse

### Skills Learned

- Kerberoasting mitigation
- Password auditing
- Active Directory attack awareness

---

## Task 7 – Windows AD Hardening Cheat Sheet

### Topics Reviewed

- Least Privilege
- Secure Authentication
- Known Attack Mitigation
- Microsoft Security Compliance Toolkit
- Windows Update importance

### Skills Learned

- Enterprise hardening workflow
- Security best practices
- Hardening checklist

---

# Troubleshooting

## Browser Client Authentication Failure

### Issue

During the room, the browser-based lab environment failed to connect successfully.

Observed symptoms included:

- Authentication Failed
- Failed to communicate with server
- Windows VM loading issues
- AttackBox session instability

### Investigation

Verified:

- Lab machine status
- Browser session
- Windows VM availability

### Resolution

- Switched from Chrome to Firefox
- Established a new browser session
- Successfully connected to the Windows VM
- Continued the lab without further issues

### Lessons Learned

Infrastructure or browser session issues can resemble authentication problems. Before troubleshooting Active Directory itself, verify the lab environment is functioning correctly.

---

# Key Concepts Learned

- Active Directory security boundaries
- Authentication hardening
- LAN Manager hash protection
- SMB Signing
- LDAP Signing
- Password rotation
- Password policies
- Least Privilege
- RBAC
- Tiered Administration
- Microsoft Security Baselines
- Policy Analyzer
- Kerberoasting
- Password auditing

---

# Tools Used

- Windows Server
- Group Policy Management Editor
- PowerShell ISE
- Microsoft Security Compliance Toolkit
- Policy Analyzer
- Password Audit Report

---

# Screenshots

## Troubleshooting

- active-directory-hardening-authentication-failed
- active-directory-hardening-lab-connection-restored

## Authentication Hardening

- active-directory-hardening-task03-lm-hash-storage-disabled
- active-directory-hardening-task03-smb-signing-enabled
- active-directory-hardening-task03-ldap-signing-required
- active-directory-hardening-task03-password-policy-viewed
- active-directory-hardening-task03-authentication-hardening-policies

## Microsoft Security Compliance Toolkit

- active-directory-hardening-task05-msct-script-analysis-baseline
- active-directory-hardening-task05-msct-script-analysis-merge-policy

## Password Auditing

- active-directory-hardening-task06-password-audit-report

## Room Summary

- active-directory-hardening-task07-hardening-cheat-sheet

## Completion

- active-directory-hardening-room-complete

---

# Skills Developed

- Active Directory administration
- Group Policy Management
- Authentication security
- Windows security hardening
- Microsoft Security Compliance Toolkit
- Policy Analyzer
- Password policy management
- Enterprise security baselines
- Least Privilege implementation
- RBAC
- Tiered Administration
- Password auditing
- Kerberoasting mitigation
- Security troubleshooting

---

# Personal Reflection

This room provided a practical introduction to securing Active Directory using Microsoft's recommended best practices. Configuring authentication security policies and reviewing Microsoft's Security Compliance Toolkit demonstrated how enterprise administrators standardize and enforce secure configurations through Group Policy. The troubleshooting experience also reinforced the importance of validating the lab environment before assuming configuration errors.

---

# Room Summary

✅ Active Directory Hardening completed successfully.

Core focus areas included:

- Authentication hardening
- Least Privilege
- Microsoft Security Compliance Toolkit
- Enterprise password policies
- Group Policy security settings
- Active Directory attack mitigation
- Security best practices