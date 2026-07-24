# Monitoring & Logging Active Directory

## Status

✅ Completed

---

# Room Information

| Category | Value |
|----------|-------|
| Platform | TryHackMe |
| Type | Standalone Room |
| Difficulty | Easy |
| Focus | Active Directory Monitoring, Windows Event Logs, Splunk, Blue Team |

---

# Overview

This room introduced Active Directory monitoring from a defender's perspective by exploring the protocols, Windows Event IDs, and audit policies that generate security telemetry within an enterprise environment.

Rather than focusing solely on authentication, the room demonstrated how defenders correlate authentication events, account lifecycle events, group membership changes, and directory service modifications to investigate user activity and identify suspicious behavior.

Practical exercises were completed using Splunk to query Windows Security Events, establish baseline activity, perform stack counting, and investigate a realistic user onboarding scenario.

---

# Learning Objectives

- Understand Active Directory authentication traffic
- Identify Kerberos and NTLM authentication events
- Interpret common Windows Security Event IDs
- Configure and verify Windows Advanced Audit Policies
- Establish baseline activity for Active Directory environments
- Use stack counting to identify anomalies
- Investigate user activity using Splunk
- Correlate multiple security events into an investigation timeline

---

# Technologies Used

- Active Directory
- Windows Security Event Logs
- Kerberos
- NTLM
- LDAP
- SMB
- RDP
- Splunk Enterprise
- Windows Advanced Audit Policies

---

# Key Event IDs

| Event ID | Description |
|-----------|-------------|
| 4624 | Successful Logon |
| 4625 | Failed Logon |
| 4720 | Account Created |
| 4722 | Account Enabled |
| 4724 | Password Reset |
| 4725 | Account Disabled |
| 4728 | Global Security Group Membership |
| 4732 | Local Security Group Membership |
| 4756 | Universal Security Group Membership |
| 4768 | Kerberos Ticket Granting Ticket (TGT) |
| 4769 | Kerberos Service Ticket |
| 4771 | Kerberos Pre-Authentication Failure |
| 4776 | NTLM Credential Validation |
| 5136 | Directory Service Object Modified |
| 5140 | File Share Access |

---

# Practical Activities

Completed the following practical investigations:

- Queried Kerberos Ticket Granting Ticket requests
- Investigated NTLM authentication validation
- Reviewed successful NTLM logons
- Counted unique Kerberos authentication accounts
- Investigated account creation events
- Reviewed security group membership changes
- Investigated Active Directory object modifications
- Reviewed successful logon distributions
- Compared computer account activity vs user activity
- Performed stack counting analysis
- Investigated Kerberos service usage
- Reviewed Kerberos encryption types
- Investigated user onboarding activity

---

# Additional Splunk Investigations

Beyond the required room tasks, additional analysis was performed to better understand authentication patterns and baseline activity.

## Kerberos Authentication Analysis

Investigated:

- Ticket Granting Ticket requests
- Unique user accounts
- Client IP addresses
- Ticket encryption types

Findings:

- 14 unique accounts requested TGTs
- All observed tickets used AES-256 (0x12)
- Client `::ffff:10.5.50.12` generated the highest number of service ticket requests

---

## NTLM Authentication Investigation

Investigated:

- NTLM credential validation
- Successful NTLM logons
- Source workstations
- Source network addresses

Observed how NTLM authentication differs from Kerberos authentication while identifying the originating workstation for each authentication attempt.

---

## Baseline Development

Performed additional baseline analysis by reviewing:

- Most active client addresses
- Most requested services
- Encryption type distribution
- Unique users per service

Key observations:

- THM-DC$ was the most frequently requested service
- Computer accounts generated significant authentication traffic
- Modern AES encryption was consistently used throughout the dataset

---

# Investigation Scenario

Performed an onboarding audit for a newly created employee account.

## Findings

| Investigation | Result |
|--------------|--------|
| New User | nathan.brooks |
| Created By | adm-luke.sullivan |
| Assigned Group | Marketing |
| First Kerberos Source | ::ffff:10.5.50.12 |

The investigation demonstrated how multiple Windows Event IDs can be correlated to reconstruct user activity from account creation through first authentication.

---

# Engineering Challenges

No significant technical issues were encountered during the lab.

The primary challenge involved understanding how individual Windows Event IDs relate to one another during a complete authentication and account lifecycle process.

---

# Troubleshooting Process

Rather than relying solely on the provided queries, additional Splunk investigations were performed to validate understanding.

Additional analysis included:

- Counting unique Kerberos accounts
- Reviewing authentication sources
- Comparing encryption types
- Measuring service usage
- Building baseline activity

These investigations reinforced how defenders move beyond individual events to understand broader patterns.

---

# Resolution

By correlating multiple event types, it was possible to:

- Identify newly created users
- Verify administrative actions
- Track group membership changes
- Trace initial authentication activity
- Establish baseline authentication behavior

---

# Skills Demonstrated

- Active Directory Monitoring
- Windows Event Log Analysis
- Splunk Searching
- Splunk Statistics
- Event Correlation
- Kerberos Investigation
- NTLM Investigation
- Authentication Analysis
- Baseline Development
- Threat Hunting
- Security Monitoring
- Blue Team Investigation

---

# Lessons Learned

- Authentication events provide only one part of an investigation.
- Correlating multiple Windows Event IDs creates a complete activity timeline.
- Baseline analysis is essential for identifying anomalies.
- Computer accounts generate a significant percentage of authentication traffic.
- Proper audit policy configuration is required to capture valuable forensic evidence.
- Stack counting is an effective technique for identifying rare and potentially suspicious activity.

---

# Interview Talking Points

## Objective

Investigate Active Directory authentication activity and user lifecycle events using Windows Event Logs and Splunk.

## Challenge

Understand how multiple Windows Security Event IDs relate to one another and distinguish normal authentication activity from potentially suspicious behavior.

## Investigation

Performed authentication analysis, baseline development, event correlation, and user onboarding verification using Splunk.

## Resolution

Successfully reconstructed user activity from account creation through first authentication while validating account creation, group membership, and authentication source.

## Skills Demonstrated

- Windows Event Log Analysis
- Active Directory Monitoring
- Splunk Investigation
- Threat Hunting
- Event Correlation
- Blue Team Operations

---

# Personal Reflection

This room reinforced that effective monitoring depends on understanding normal behavior before searching for anomalies.

The additional Splunk investigations performed beyond the room requirements provided valuable experience using statistical analysis, event correlation, and baseline development techniques that closely resemble real-world SOC workflows.

Rather than simply identifying individual Windows Event IDs, the room demonstrated how defenders combine multiple events to build an investigative timeline and understand user behavior within an Active Directory environment.