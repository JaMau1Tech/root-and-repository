# Windows Fundamentals 1
 
**Room:** [Windows Fundamentals 1](https://tryhackme.com/room/windowsfundamentals1xbx)
**Platform:** TryHackMe
**Collection:** Windows Fundamentals
**Status:** ✅ Complete
**Completed Tasks:** 10 / 10
**Points Earned:** 104
**Target VM:** Windows Server 2019 Standard
 
---
 
## Room Overview
 
Windows Fundamentals 1 is an introductory room covering the foundations of the Windows operating system: version history and end-of-life risk, the Desktop GUI, the NTFS file system, user accounts and local permissions, User Account Control (UAC), Settings vs. Control Panel, and Task Manager. The lab environment is a Windows Server 2019 Standard VM, accessed via TryHackMe's AttackBox or Remote Desktop Protocol (RDP).
 
---
 
## Key Concepts
 
- **Windows version lifecycle:** XP → Vista → 7 → 8.x → 10 → 11, with a parallel Server line (currently Windows Server 2025). End-of-life (EOL) means the end of security patching, which directly expands attack surface.
- **Desktop GUI components:** Desktop, Start Menu, Search Box, Task View, Taskbar, Toolbars, Notification Area — each independently configurable via right-click context menus (Personalize for appearance, Display settings for resolution/multi-monitor).
- **NTFS (New Technology File System):** a journaling file system that can self-repair via a log after a failure (unlike FAT). Supports files >4GB, granular permissions, compression, and encryption (EFS/BitLocker).
- **NTFS permissions:** Full control, Modify, Read & Execute, List folder contents, Read, Write — viewed via Properties → Security tab.
- **Alternate Data Streams (ADS):** a hidden, additional data stream attached to an NTFS file. Not shown in File Explorer by default. Used legitimately (e.g., the "downloaded from the internet" Zone.Identifier flag) and maliciously (hiding payloads).
- **Environment variables:** `%windir%` points to the Windows install directory, making paths portable regardless of drive letter or install location.
- **System32:** the critical OS binaries/DLLs folder inside `%windir%`; a common target for stealth and "living off the land" techniques due to the trust and volume of legitimate files there.
- **User account types:** Administrator (full system control) vs. Standard User (own files/folders only, no system-level changes). Profiles are created automatically at `C:\Users\<username>` on first login.
- **Local group management (`lusrmgr.msc`):** permissions are assigned via group membership rather than per-user, enabling inheritance and easier administration. This is distinct from Group Policy Objects (GPOs), which push policy at the domain level via Active Directory — this lab machine is standalone/non-domain, so only local group permissions apply.
- **Built-in Guest account:** the default guest-access account; a known, predictable target that should be disabled (not just password-protected) in production environments.
- **User Account Control (UAC):** introduced in Windows Vista. Even administrator accounts run non-elevated by default; privileged actions trigger a confirmation prompt. UAC does **not** apply to the built-in local Administrator account, which is always elevated — a key reason that account should not be used for daily work.
- **Settings vs. Control Panel:** Settings is the modern, touch-first interface (introduced in Windows 8); Control Panel is the legacy interface with more advanced/granular options. Some Settings paths redirect into Control Panel. Programs and Features is the authoritative source for installed software — more reliable than desktop shortcuts, which can be stale, missing, or orphaned.
- **Task Manager:** Simple View vs. More details. The Performance tab tracks CPU, Memory, Disk, and Network utilization. The Startup tab is a key location for identifying malware persistence mechanisms.
---
 
## Commands / Tools Used
 
| Tool / Command | Purpose |
|---|---|
| `lusrmgr.msc` | Local Users and Groups management console |
| Ctrl+Shift+Esc | Task Manager keyboard shortcut |
| RDP | Remote access to the lab VM using provided credentials |
 
---
 
## Administrative Tasks Performed
 
- Connected to the lab VM via AttackBox and RDP
- Reviewed NTFS properties and Security tab permissions on `C:\Windows` and `C:` drive
- Explored `System32` and `Windows` folder contents
- Enumerated local user accounts and group membership via `lusrmgr.msc` (identified `tryhackmebilly` as the standard user, member of Remote Desktop Users and Users groups)
- Logged in as the standard user via RDP and observed the UAC elevation prompt when attempting to install Wireshark
- Navigated Control Panel (Category and Small Icons views) and Windows Settings to compare interfaces
- Reviewed Programs and Features for installed software inventory
- Reviewed Network Connections via Control Panel
- Opened Task Manager in both Simple and More details views to review running processes and resource usage
---
 
## Security Concepts Covered
 
- EOL software risk and patch management
- NTFS permissions model and Alternate Data Streams as a data-hiding technique
- Built-in Administrator and Guest account risk (always-elevated Administrator, predictable Guest account)
- Local group-based permission inheritance vs. GPO-based domain policy
- UAC as a privilege-escalation control and its exemption for the built-in Administrator account
- Task Manager's Startup tab as a malware persistence indicator
- Programs and Features as a ground-truth software inventory versus unreliable desktop shortcuts
---
 
## Engineering Challenges
 
No significant technical errors, misconfigurations, or troubleshooting occurred during this room — all tasks completed as expected using the provided lab credentials and documented navigation paths.
 
---
 
## Lessons Learned
 
- Environment variables like `%windir%` exist specifically to make paths portable — the same underlying logic scales up to scripting and detection engineering in later, more advanced rooms.
- UAC's exemption for the built-in Administrator account is a concrete, memorable justification for the broader hardening principle of not using that account for daily work.
- Local group permissions (via `lusrmgr.msc`) and GPOs are two distinct Windows access-control mechanisms — local group membership applies on standalone machines, while GPOs require Active Directory and apply domain-wide. Keeping this distinction clear now avoids confusion in upcoming Active Directory-focused rooms.
- ADS visibility is a File Explorer display gap, not a permissions restriction — a subtle distinction worth remembering for later forensics/malware-analysis contexts.
---
 
## Interview Talking Points
 
- **Objective:** Build foundational familiarity with the Windows operating system — file system architecture (NTFS), user account and permission models, UAC, and core administrative interfaces (Settings, Control Panel, Task Manager) — using a hands-on Windows Server 2019 lab environment.
- **Challenge:** No major technical obstacles arose; the primary learning challenge was building precise, defensible explanations for *why* certain Windows behaviors exist (e.g., why UAC exempts the built-in Administrator account, why local group permissions differ from GPOs) rather than just what the behaviors are.
- **Investigation:** Worked through each Windows administrative interface directly in the lab VM — comparing Settings vs. Control Panel, inspecting NTFS permissions via the Security tab, and enumerating local users/groups via `lusrmgr.msc` — to build a first-hand mental model rather than relying on the room's written explanations alone.
- **Resolution:** Completed all 10 tasks, correctly identifying NTFS permissions, ADS behavior, the `%windir%` environment variable, local user/group structure, the UAC elevation flow, and Task Manager's persistence-relevant tabs.
- **Skills Demonstrated:** Windows file system architecture (NTFS, ADS), local user and group administration, UAC and privilege escalation controls, Windows administrative interface navigation (Settings, Control Panel, Task Manager), and foundational Windows security reasoning applicable to both offensive and defensive contexts.
---
 
**Documentation Standard:** Root & Repository Standalone TryHackMe Workflow v3.1
