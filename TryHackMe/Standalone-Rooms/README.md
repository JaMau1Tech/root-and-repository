# Standalone Rooms

This directory contains documentation for TryHackMe standalone rooms, organized into topic-based collections. Unlike structured learning paths, standalone rooms focus on individual technologies, platforms, and techniques — each collection groups related rooms together under a shared README and image library.

---

## Collections

| Collection | Progress | Status |
|------------|:--------:|:------:|
| Active Directory | 3 / 3 Rooms | ✅ Complete |
| Windows Fundamentals | 3 / 3 Rooms | ✅ Complete |
| Linux Fundamentals | 1 / 3 Rooms | 🚧 In Progress |

---

## Active Directory

Focuses on Microsoft's enterprise identity and access management platform — administering Windows domains, managing users and computers, configuring Group Policy, securing Active Directory environments, and monitoring enterprise infrastructure.

- ✅ Windows Active Directory Basics
- ✅ Active Directory Hardening
- ✅ Monitoring Active Directory

**Progress:** 3 / 3 Rooms Completed (100%)

---

## Windows Fundamentals

Covers core Windows operating system concepts and administration — the Desktop GUI, the NTFS file system, user accounts and local permissions, User Account Control (UAC), Settings and Control Panel, Task Manager, System Configuration, Computer Management, System Information, Resource Monitor, Command Prompt, the Windows Registry, and the built-in Windows security stack (Windows Update, Windows Security/Defender, Firewall, SmartScreen, Device Security, BitLocker, VSS).

- ✅ Windows Fundamentals 1
- ✅ Windows Fundamentals 2
- ✅ Windows Fundamentals 3

**Progress:** 3 / 3 Rooms Completed (100%)

---

## Linux Fundamentals

Covers core Linux operating system concepts through the terminal — command-line navigation, file and content searching, output redirection, and shell operators. Entirely terminal-driven, reflecting Linux's dominance in server, cloud, and embedded environments.

- ✅ Linux Fundamentals (Pt1)
- ⏳ Linux Fundamentals (Pt2)
- ⏳ Linux Fundamentals (Pt3)

**Progress:** 1 / 3 Rooms Completed (33%)

---

## Repository Structure

```text
Standalone-Rooms/
│
├── README.md
│
├── Active-Directory/
│   ├── README.md
│   ├── images/
│   ├── Windows-Active-Directory-Basics/
│   ├── Active-Directory-Hardening/
│   └── Monitoring-Active-Directory/
│
├── Windows-Fundamentals/
│   ├── README.md
│   ├── images/
│   ├── Windows-Fundamentals-1/
│   ├── Windows-Fundamentals-2/
│   └── Windows-Fundamentals-3/
│
└── Linux-Fundamentals/
    ├── README.md
    ├── images/
    └── Linux-Fundamentals-1/
```

---

## Documentation Standards

All rooms in this directory follow the **Root & Repository Standalone TryHackMe Workflow v3.1**: each completed room produces a `task-notes.md` file documenting the engineering process (concepts, administrative tasks, troubleshooting, lessons learned, and interview talking points), with supporting screenshots cataloged in each collection's shared images README.

---

**Documentation Standard:** Root & Repository Standalone TryHackMe Workflow v3.1