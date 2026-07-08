# Troubleshooting Guide

This document records issues encountered during the Linux virtual machine and WSL setup process.

---

# Issue 1 - Xubuntu Installer Freeze

## Problem

The Xubuntu installer became unresponsive during installation inside Oracle VirtualBox.

## Symptoms

- Installer stopped progressing
- Loading spinner froze
- Desktop environment failed to load
- Installation could not continue normally

## Investigation

Possible causes considered:

- Display driver incompatibility
- VirtualBox graphics settings
- Insufficient video memory
- Operating system compatibility issues

## Steps Attempted

- Restarted the virtual machine
- Verified ISO download
- Adjusted display settings
- Increased video memory
- Booted with Safe Graphics Mode

## Resolution

Booted the installer using:

```text
Ubuntu Safe Graphics
```

## Result

The installer launched successfully and the desktop environment loaded correctly.

---

# Issue 2 - WSL Feature Name Unknown

## Problem

Attempted to enable WSL manually using DISM:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

Received:

```text
Feature name Microsoft-Windows-Subsystem-Linux is unknown.
```

## Investigation

Checked available Windows features:

```powershell
DISM /Online /Get-Features /Format:Table | findstr /i "linux"
DISM /Online /Get-Features /Format:Table | findstr /i "virtual"
```

Findings:

```text
Microsoft-Windows-Subsystem-Linux | Disabled
VirtualMachinePlatform | Enabled
```

## Resolution

Restarted Windows and re-ran WSL commands.

## Result

WSL was recognized properly after reboot.

---

# Issue 3 - WSL Installation Appeared Frozen

## Problem

Ubuntu installation through WSL appeared stuck at:

```text
49.1%
```

## Resolution

Pressed:

```text
Ctrl + C
```

The installation immediately completed successfully.

## Lesson Learned

Terminal output may not always accurately reflect the real installation state.

---

# Skills Practiced

- Troubleshooting
- Virtualization
- PowerShell
- DISM commands
- Windows administration
- Linux installation
- Documentation
