# Ubuntu/Xubuntu Virtual Machine Installation Guide

This document outlines the process used to create a Linux virtual machine with Oracle VirtualBox.

---

# Objective

Build a Linux virtual machine for:

- Learning Linux fundamentals
- Practicing cybersecurity concepts
- Creating a home lab environment
- Developing troubleshooting skills
- Documenting technical work

---

# Requirements

## Software

- Oracle VirtualBox
- Xubuntu ISO
- Windows 11 host machine

---

# Installation Steps

## Step 1 - Download Oracle VirtualBox

Downloaded and installed Oracle VirtualBox on the Windows host machine.

## Step 2 - Download Xubuntu ISO

Downloaded the Xubuntu installation image.

## Step 3 - Create a New Virtual Machine

Created a new virtual machine named:

```text
Cyber-Lab-Ubuntu
```

Selected:

```text
Linux
Ubuntu 64-bit
```

## Step 4 - Configure Hardware

Allocated:

- 2048 MB RAM
- 1 CPU Core
- 25 GB Virtual Hard Disk

## Step 5 - Attach Installation Media

Mounted the Xubuntu ISO file to the virtual optical drive.

## Step 6 - Start the Virtual Machine

Booted the virtual machine for the first time.

## Step 7 - Complete Installation

Followed the installer prompts to configure the operating system and create a user account.

---

# Installation Issue

The installer became unresponsive during setup.

The issue was resolved by booting with:

```text
Ubuntu Safe Graphics
```

Detailed troubleshooting is documented in:

```text
docs/troubleshooting.md
```

---

# Result

The virtual machine successfully booted into the Linux desktop environment.

---

# Lessons Learned

- Virtual machines require correct hardware and display configuration.
- Safe Graphics Mode can resolve Linux installer display issues.
- Documentation makes future installations easier to repeat.
