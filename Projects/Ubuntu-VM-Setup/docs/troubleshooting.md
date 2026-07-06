# Troubleshooting Guide

This document records the issues encountered during the Ubuntu virtual machine installation and the steps taken to resolve them.

---

# Problem

The Ubuntu installer repeatedly froze during installation inside Oracle VirtualBox.

Symptoms included:

- Installer becoming unresponsive
- Loading spinner hanging indefinitely
- Desktop environment failing to load properly
- Installation not progressing

---

# Environment

## Host Operating System

```text
Windows 11
```

## Virtualization Platform

```text
Oracle VirtualBox
```

## Guest Operating System

```text
Xubuntu 26.04
```

---

# Troubleshooting Steps Attempted

## Restarted the Virtual Machine

Rebooted the virtual machine and attempted the installation again.

Result:

```text
Issue persisted.
```

---

## Adjusted VirtualBox Display Settings

Reviewed and modified:

- Graphics controller settings
- Display configuration
- Video memory allocation

Result:

```text
Issue persisted.
```

---

## Increased Video Memory

Increased video memory allocation to:

```text
128 MB
```

Result:

```text
Issue persisted.
```

---

## Verified ISO Download

Confirmed that the Xubuntu ISO file was downloaded correctly and was not corrupted.

Result:

```text
ISO was valid.
```

---

# Resolution

Booted the operating system using:

```text
Ubuntu (Safe Graphics)
```

Result:

```text
Installer launched successfully.
Desktop environment loaded correctly.
Installation completed successfully.
```

---

# Root Cause

The issue appeared to be related to:

- Display compatibility
- Graphics driver configuration
- VirtualBox graphics settings

Safe Graphics Mode bypassed the issue and allowed the operating system to install properly.

---

# Lessons Learned

- Safe Graphics Mode should be attempted when Ubuntu experiences graphical issues inside VirtualBox.
- Virtual machine display settings can significantly impact operating system installation.
- Troubleshooting often requires testing multiple solutions.
- Documenting every troubleshooting step makes future issues easier to resolve.

---

# Skills Practiced

- Troubleshooting
- Problem solving
- Virtualization
- Linux installation
- Documentation
- Research and investigation

---

# Cybersecurity Relevance

Troubleshooting is a critical cybersecurity skill because security professionals regularly encounter:

- System failures
- Configuration issues
- Software incompatibilities
- Unexpected behavior during tool installations

Being able to methodically investigate and document problems is an essential skill in both IT and cybersecurity.

---

# Future Improvements

- Create VirtualBox snapshots before making major changes.
- Experiment with additional display configurations.
- Build additional Linux virtual machines for practice.
- Continue documenting all issues and resolutions.