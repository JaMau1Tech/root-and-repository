# Windows Fundamentals 2

**Room:** [Windows Fundamentals 2](https://tryhackme.com/room/windowsfundamentals2x0x)
**Platform:** TryHackMe
**Collection:** Windows Fundamentals
**Status:** ✅ Complete
**Completed Tasks:** 9 / 9
**Target VM:** Windows Server 2019 Standard (WINFUN2)

---

## Room Overview

Windows Fundamentals 2 continues directly from Room 1, moving from desktop basics into deeper administrative tooling: System Configuration (`msconfig`) and Advanced System Settings, User Account Control settings, Computer Management, System Information, Resource Monitor, Command Prompt, and the Windows Registry.

---

## Key Concepts

- **System Configuration (`msconfig`):** five tabs — General (Normal/Diagnostic/Selective startup modes), Boot, Services, Startup (unreliable on Windows Server — use `shell:startup` instead), and Tools (direct launch commands for other admin utilities). Functions as a structured troubleshooting methodology: isolate an issue by selectively disabling services/startup items and restarting between each test, rather than hand-editing the registry directly.
- **Advanced System Settings:** page file (virtual memory) configuration, and Startup and Recovery settings controlling crash dump behavior (Automatic, Kernel, Small, Complete, or None memory dump).
- **User Account Control settings (`UserAccountControlSettings.exe`):** four-level slider — Always notify (Secure Desktop, blocks malware from auto-clicking elevation prompts), Notify for apps (default), Notify without dimming, Never notify (a security posture red flag warranting investigation, not proof of compromise on its own).
- **Computer Management (`compmgmt.msc`):** three sections — System Tools (Task Scheduler, Event Viewer, Shared Folders, Local Users and Groups, Performance, Device Manager), Storage (Disk Management, Windows Server Backup — Server-specific), and Services and Applications (Services with Startup type Automatic/Manual/Disabled, WMI Control).
- **Event Viewer:** three-pane layout; five event types (Error, Warning, Information, Success Audit, Failure Audit); four standard logs (Application, Security, System, CustomLog) — Security log stays empty until audit policies are explicitly configured.
- **Default administrative shares (`C$`, `ADMIN$`):** enabled by default on every Windows machine, relevant to lateral movement due to predictable paths and native execution vectors.
- **System Information (`msinfo32.exe`):** three sections — Hardware Resources, Components (searchable), Software Environment (includes Environment Variables and Network Connections). `ComSpec` environment variable resolves to the command interpreter path.
- **Resource Monitor (`resmon.exe`):** deeper per-process resource view than Task Manager across four tabs (CPU, Memory, Disk, Network); Associated Handles search (under the CPU tab) identifies which process has a specific file locked open.
- **Command Prompt:** `hostname`, `whoami`, `ipconfig` (`/all` for detail), `netstat`, `net` (sub-commands via `net help <subcommand>`, not `/?`). `net session` is useful for identifying active connections to a file server during an investigation.
- **Registry Editor (`regedit.exe`):** central hierarchical configuration database underlying nearly every tool in this room. Five root keys (HKCU, HKU, HKLM, HKCR, HKEY_CURRENT_CONFIG); common data types (REG_SZ, REG_DWORD, REG_BINARY, REG_MULTI_SZ); editable via GUI, Group Policy, `.reg` files, scripting, WMI, or `reg.exe`. Best practice: export/back up before editing.

---

## Commands / Tools Used

| Command | Purpose |
|---|---|
| `UserAccountControlSettings.exe` | Open UAC settings |
| `compmgmt.msc` | Open Computer Management |
| `msinfo32.exe` | Open System Information |
| `resmon.exe` | Open Resource Monitor |
| `regedit.exe` | Open Registry Editor |
| `ipconfig /all` | Detailed network configuration |
| `hostname`, `whoami`, `netstat`, `net`, `net help <subcommand>` | Command Prompt system/network queries |
| `systeminfo` | Full system summary (Registered Owner, System Name, etc.) via Command Prompt |
| `shell:startup` | Direct access to the Startup folder (Server OS workaround) |

---

## Administrative Tasks Performed

- Explored `msconfig`'s five tabs, confirming Server-specific behavior (empty Startup tab) and verifying startup items via `shell:startup`
- Reviewed Advanced System Settings: page file configuration and crash dump (Startup and Recovery) settings
- Located the "Systems Internals" manufacturer service in `msconfig`'s Services tab and confirmed license/registration details via `systeminfo`
- Adjusted and reviewed the UAC settings slider and its four security levels
- Navigated Computer Management's three sections, including Device Manager, Disk Management, and Event Viewer's Overview and Summary
- Identified the `npcapwatchdog` scheduled task trigger and a hidden shared folder via Shared Folders
- Reviewed environment variables (`ComSpec`) and used `msinfo32`'s search feature
- Reviewed Resource Monitor's four resource tabs conceptually
- Practiced Command Prompt queries (`hostname`, `whoami`, `ipconfig`, `netstat`, `net`, `systeminfo`)
- Reviewed Registry Editor's structure: root keys, hives, and data types

---

## Security Concepts Covered

- UAC Secure Desktop as an anti-automation control against malware self-elevation
- "Never notify" UAC as a security posture indicator requiring further investigation, not a standalone compromise conclusion
- Default administrative shares (`C$`, `ADMIN$`) as a lateral movement vector
- Unexpectedly disabled critical services as a potential tampering/evasion indicator — document before remediating, since resetting a setting during an active investigation can destroy evidence
- Event Viewer's Security log requiring explicit audit policy configuration to populate (ties directly to the Monitoring Active Directory collection)
- Registry as an unvalidated, unprotected configuration layer — export/back up before editing
- `net session` as an investigative tool for identifying active file server connections
- Resource Monitor's Associated Handles search as a way to identify which process holds a specific file open

---

## Engineering Challenges

No significant technical errors or troubleshooting occurred during this room. The primary friction points were conceptual/retention-based: refining precise reasoning around UAC risk indicators, appropriate response to a disabled critical service during an investigation, and exact terminology (Resource Monitor's Associated Handles feature vs. the general "process analysis" description).

---

## Lessons Learned

- Distinguishing a security *indicator* (e.g., "Never notify," a disabled service) from a security *conclusion* (e.g., "compromised") is a recurring and important discipline — investigative claims should stay proportional to the evidence at hand.
- During an active investigation, the instinct to immediately "fix" something (like re-enabling a disabled service) can destroy evidence — document first, remediate second.
- Precise terminology matters for interview-readiness — "Associated Handles" is a more defensible, specific answer than a paraphrased description of the underlying capability.
- The Registry is the common substrate underneath every GUI tool covered in this room, which clarifies why GUI tools function as safer, validated front-ends over direct registry edits.

---

## Interview Talking Points

- **Objective:** Build practical familiarity with Windows' deeper administrative toolset — System Configuration, Computer Management, System Information, Resource Monitor, Command Prompt, and the Registry — extending the foundational knowledge from Windows Fundamentals 1.
- **Challenge:** No major technical obstacles arose; the primary challenge was calibrating investigative reasoning — avoiding overstated conclusions from single indicators (e.g., a UAC setting or a disabled service) without corroborating evidence.
- **Investigation:** Worked directly through each admin tool in the lab VM — msconfig's five tabs, Computer Management's three sections, System Information's searchable components, and Registry Editor's structure — building hands-on familiarity rather than relying on written descriptions alone.
- **Resolution:** Completed all 9 tasks, correctly identifying UAC configuration commands, Computer Management navigation, crash dump settings, environment variables, and command-line diagnostic tools; refined two investigative reasoning gaps through retention review.
- **Skills Demonstrated:** Windows advanced administrative tooling (msconfig, Computer Management, System Information, Resource Monitor), Registry structure and risk awareness, UAC security posture analysis, Command Prompt diagnostics, and foundational incident-investigation discipline (evidence preservation before remediation).

---

**Documentation Standard:** Root & Repository Standalone TryHackMe Workflow v3.1