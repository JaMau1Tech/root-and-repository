# Images

This directory contains all screenshots for the **Active Directory** standalone TryHackMe collection.

Screenshots document practical administration, security configuration, troubleshooting, auditing, and room completion. They provide visual evidence of hands-on work completed during each room.

---

# Screenshot Standards

Screenshots are captured only for meaningful activities, including:

- Administrative configuration
- Group Policy changes
- Security policy implementation
- Authentication hardening
- Microsoft security tools
- Password auditing
- Troubleshooting
- Room completion

Screenshots are **not** taken for reading-only tasks or multiple-choice questions unless they demonstrate a practical concept.

---

# Windows Active Directory Basics

## Room Status

✅ Completed

### Screenshots

| Screenshot | Description |
|------------|-------------|
| *(Screenshots from the Windows Active Directory Basics room.)* |

---

# Active Directory Hardening

## Room Status

✅ Completed

### Troubleshooting

| Screenshot | Description |
|------------|-------------|
| `active-directory-hardening-authentication-failed` | Browser client authentication failure before troubleshooting. |
| `active-directory-hardening-lab-connection-restored` | Successful recovery after establishing a new browser session. |

---

### Task 3 – Securing Authentication Methods

| Screenshot | Description |
|------------|-------------|
| `active-directory-hardening-task03-lm-hash-storage-disabled` | Disabled storage of LAN Manager password hashes. |
| `active-directory-hardening-task03-smb-signing-enabled` | Enabled SMB signing for secure SMB communications. |
| `active-directory-hardening-task03-ldap-signing-required` | Required LDAP signing on the domain controller. |
| `active-directory-hardening-task03-password-policy-viewed` | Reviewed the default domain password policy. |
| `active-directory-hardening-task03-authentication-hardening-policies` | Summary view of authentication hardening policies configured through Group Policy. |

---

### Task 5 – Microsoft Security Compliance Toolkit

| Screenshot | Description |
|------------|-------------|
| `active-directory-hardening-task05-msct-script-analysis-baseline` | Reviewed the `BaselineLocalInstall.ps1` script in PowerShell ISE. |
| `active-directory-hardening-task05-msct-script-analysis-merge-policy` | Reviewed the `Merge-PolicyRules.ps1` script in PowerShell ISE. |

---

### Task 6 – Protecting Against Known Attacks

| Screenshot | Description |
|------------|-------------|
| `active-directory-hardening-task06-password-audit-report` | Reviewed the generated password audit report and password reuse findings. |

---

### Task 7 – Windows AD Hardening Cheat Sheet

| Screenshot | Description |
|------------|-------------|
| `active-directory-hardening-task07-hardening-cheat-sheet` | Final Active Directory hardening reference guide. |

---

### Room Completion

| Screenshot | Description |
|------------|-------------|
| `active-directory-hardening-room-complete` | Successful completion of the Active Directory Hardening room. |

---

# Monitoring Active Directory

## Room Status

⏳ Not Started

Screenshots will be added after completing the room.

---

# Screenshot Statistics

| Collection | Count |
|-----------|------:|
| Windows Active Directory Basics | *(Existing screenshots)* |
| Active Directory Hardening | 12 |
| Monitoring Active Directory | 0 |
| **Current Total** | **12 + Windows Active Directory Basics screenshots** |

---

# Documentation Notes

- Screenshots are stored in a shared directory for the entire Active Directory collection.
- Filenames use lowercase letters and hyphens for consistency.
- Each screenshot corresponds to a meaningful administrative, security, auditing, troubleshooting, or completion milestone.
- The troubleshooting screenshots document a browser/session connectivity issue encountered during the lab and the successful recovery, illustrating real-world troubleshooting alongside Active Directory hardening tasks.