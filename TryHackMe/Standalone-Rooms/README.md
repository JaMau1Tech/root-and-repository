# Standalone Rooms

This directory contains documentation for TryHackMe standalone rooms, organized into topic-based collections. Unlike structured learning paths, standalone rooms focus on individual technologies, platforms, and techniques — each collection groups related rooms together under a shared README and image library.

---

## Collections

| Collection | Progress | Status |
|------------|:--------:|:------:|
| Active Directory | 3 / 3 Rooms | ✅ Complete |
| Windows Fundamentals | 2 / 3 Rooms | 🚧 In Progress |

---

## Active Directory

Focuses on Microsoft's enterprise identity and access management platform — administering Windows domains, managing users and computers, configuring Group Policy, securing Active Directory environments, and monitoring enterprise infrastructure.

- ✅ Windows Active Directory Basics
- ✅ Active Directory Hardening
- ✅ Monitoring Active Directory

**Progress:** 3 / 3 Rooms Completed (100%)

---

## Windows Fundamentals

Covers core Windows operating system concepts and administration — the Desktop GUI, the NTFS file system, user accounts and local permissions, User Account Control (UAC), Settings and Control Panel, Task Manager, System Configuration, Computer Management, System Information, Resource Monitor, Command Prompt, and the Windows Registry.

- ✅ Windows Fundamentals 1
- ✅ Windows Fundamentals 2
- ⏳ Windows Fundamentals 3

**Progress:** 2 / 3 Rooms Completed (67%)

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
└── Windows-Fundamentals/
    ├── README.md
    ├── images/
    ├── Windows-Fundamentals-1/
    └── Windows-Fundamentals-2/
```

---

## Documentation Standards

All rooms in this directory follow the **Root & Repository Standalone TryHackMe Workflow v3.1**: each completed room produces a `task-notes.md` file documenting the engineering process (concepts, administrative tasks, troubleshooting, lessons learned, and interview talking points), with supporting screenshots cataloged in each collection's shared images README.

---

**Documentation Standard:** Root & Repository Standalone TryHackMe Workflow v3.1