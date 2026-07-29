# Windows Fundamentals 3

**Room:** [Windows Fundamentals 3](https://tryhackme.com/room/windowsfundamentals3xzx)
**Platform:** TryHackMe
**Collection:** Windows Fundamentals
**Status:** ✅ Complete
**Completed Tasks:** 10 / 10
**Points Earned:** 56

---

## Room Overview

Final room in the Windows Fundamentals series, covering the built-in Windows security feature stack: Windows Update, the Windows Security app overview, Virus & Threat Protection (Defender), Firewall & Network Protection, App & Browser Control (SmartScreen), Device Security (Core Isolation, TPM), BitLocker, and the Volume Shadow Copy Service (VSS).

---

## Key Concepts

- **Windows Update:** Patch Tuesday (2nd Tuesday of each month); urgent/critical patches bypass the regular schedule. Windows 10+ changed the update model so updates can be postponed but not permanently avoided. A "managed by your organization" message signals Group Policy/enterprise control over update behavior, not typical on home machines.
- **Windows Security:** central hub for all built-in protection tools, using a traffic-light status system (Green = protected, Yellow = recommendation, Red = immediate attention) across Protection areas.
- **Virus & Threat Protection:** split into Current threats (Quick/Full/Custom scans, threat history — last scan, quarantined, allowed) and Settings (Real-time protection, Cloud-delivered protection, Automatic sample submission, Controlled folder access, Exclusions, Notifications). Ransomware protection requires Controlled folder access, which in turn requires Real-time protection — a dependency chain worth remembering.
- **Firewall & Network Protection:** three independently configurable profiles — Domain (authenticates to a domain controller), Private (user-assigned, trusted/home networks), Public (default, untrusted networks like airport/coffee shop Wi-Fi). Advanced configuration via `WF.msc` (Windows Defender Firewall with Advanced Security).
- **App & Browser Control:** governs Microsoft Defender SmartScreen (states: Warn, Block, Off) — protects against phishing/malware sites and malicious downloads. Also covers Exploit protection (Control Flow Guard, DEP, ASLR), which hardens the OS against exploitation techniques at a lower level than signature-based antivirus.
- **Device Security:** Core isolation → Memory integrity, which prevents malicious code injection into high-security processes. TPM (Trusted Platform Module) is a tamper-resistant hardware crypto-processor that performs cryptographic operations independent of the OS.
- **BitLocker:** full-disk encryption, Pro/Enterprise only. Strongest protection when paired with TPM 1.2+, which both protects the encryption keys and verifies the system hasn't been tampered with while offline. Without a TPM, a removable USB drive holding the startup key is required instead.
- **Volume Shadow Copy Service (VSS):** creates shadow copies (snapshots/point-in-time copies) of data, stored in the System Volume Information folder on each protected drive. Powers restore points, system restore, and restore point management. Ransomware explicitly targets and deletes shadow copies (e.g., `vssadmin delete shadows`) to eliminate recovery options — an offline/off-site backup is the real mitigation.
- **Living Off The Land (LOTL):** the room's closing theme — attackers use legitimate, built-in Windows tools and utilities (many covered across all three Windows Fundamentals rooms) to operate while evading detection.

---

## Commands / Tools Used

| Command | Purpose |
|---|---|
| `control /name Microsoft.WindowsUpdate` | Direct launch of Windows Update settings |
| `WF.msc` | Windows Defender Firewall with Advanced Security |

---

## Administrative Tasks Performed

- Reviewed Windows Update settings, the "managed by your organization" status, and update history (2 driver updates, 2 Defender definition updates)
- Reviewed Windows Security Protection areas and identified the flagged area (Virus & threat protection)
- Reviewed Virus & Threat Protection's current threats, settings (confirmed Real-time protection off), and the Ransomware protection dependency chain
- Reviewed Firewall & Network Protection profiles (Domain/Private/Public) and the active profile under simulated public Wi-Fi conditions
- Explored the Windows Defender Firewall with Advanced Security console (`WF.msc`) and the Allowed apps list (Private/Public columns)
- Reviewed App & Browser Control's SmartScreen setting (Warn) and Exploit Protection system settings (Control Flow Guard, DEP, ASLR)
- Reviewed Device Security's Core isolation and Memory integrity toggle status
- Reviewed BitLocker's TPM dependency and the USB startup key requirement for non-TPM systems (feature not present on this lab VM)
- Located and reviewed Volume Shadow Copies configuration via right-click Local Disk (C:) → Configure Shadow Copies

---

## Security Concepts Covered

- Patch management and the shift to mandatory (postponable, not indefinitely avoidable) Windows updates
- Defender Exclusions as both a legitimate false-positive reducer and a potential attacker abuse vector
- Ransomware protection's dependency chain: Real-time protection → Controlled folder access → Ransomware protection
- Public vs. Private/Domain firewall profile risk posture, and why Windows defaults to the stricter Public profile on untrusted networks
- SmartScreen (phishing/malicious downloads) vs. signature-based antivirus as distinct, complementary protection layers
- TPM as hardware-rooted trust, underpinning BitLocker's strongest protection mode
- VSS as a documented ransomware target — direct connection to real-world attacker tradecraft
- Living Off The Land as the unifying theme across the entire Windows Fundamentals series — the same built-in tools serve both administrators and attackers depending on intent

---

## Engineering Challenges

No technical errors or troubleshooting occurred during this room.

---

## Lessons Learned

- Windows Security's traffic-light status system is a useful, fast triage pattern worth remembering as a general UX approach to surfacing security posture, not just a Windows-specific detail.
- Understanding dependency chains between security features (e.g., Real-time protection → Controlled folder access → Ransomware protection) matters for correctly diagnosing *why* a protection is unavailable, rather than treating each toggle in isolation.
- This room closes the loop on the purpose of the earlier two Windows Fundamentals rooms: the Living Off The Land framing reframes every "administrative utility" learned so far as also a potential attacker tool, depending on intent.

---

## Interview Talking Points

- **Objective:** Build practical familiarity with Windows' native security feature stack — Windows Update, Windows Security/Defender, Firewall, SmartScreen, Device Security/TPM, BitLocker, and VSS — completing the three-part Windows Fundamentals series.
- **Challenge:** No technical obstacles arose; the primary challenge was conceptual — connecting individual security features into their real-world attacker/defender context (e.g., VSS deletion in ransomware attacks, Defender exclusion abuse) rather than treating them as isolated settings.
- **Investigation:** Worked directly through Windows Security's Protection areas in the lab VM, tracing feature dependencies (e.g., why Ransomware protection required Real-time protection to be enabled first) to build a functional mental model rather than memorizing settings individually.
- **Resolution:** Completed all 10 tasks, correctly identifying Windows Update history dates, the flagged Protection area, the disabled Real-time protection setting, the active firewall profile on public networks, and BitLocker's USB startup key fallback for non-TPM systems.
- **Skills Demonstrated:** Windows Update management, Windows Security/Defender administration, Windows Firewall profile configuration, SmartScreen and Exploit Protection awareness, TPM/BitLocker security architecture, and VSS's role in ransomware resilience — completing a full foundational Windows administration and security skill set across all three Windows Fundamentals rooms.

---

**Documentation Standard:** Root & Repository Standalone TryHackMe Workflow v3.1