# WSL Migration and Troubleshooting

This document explains the decision to migrate from an unstable VirtualBox setup to Windows Subsystem for Linux.

---

# Project Overview

Ubuntu and Xubuntu virtual machines experienced installation and stability issues inside Oracle VirtualBox.

To continue learning Linux without delays, Windows Subsystem for Linux was used as a lightweight alternative.

---

# Objective

Create a stable Linux environment for:

- Linux fundamentals
- Command-line practice
- Development tools
- Cybersecurity learning
- Git and GitHub workflows

---

# Virtual Machine Problems

Issues encountered:

- Installer freezes
- Loading spinner hangs
- Display driver compatibility issues
- Virtual machine instability
- Repeated installation failures

---

# Why WSL Was Chosen

WSL provides:

- Faster startup
- Lower resource usage
- Easy Windows integration
- A real Linux command-line environment
- Strong support for development and scripting

---

# WSL Installation Commands

Checked WSL status:

```powershell
wsl --status
```

Installed WSL and Ubuntu:

```powershell
wsl --install
```

Checked Windows features:

```powershell
DISM /Online /Get-Features /Format:Table | findstr /i "linux"
DISM /Online /Get-Features /Format:Table | findstr /i "virtual"
```

---

# Final Result

Successfully installed:

- Windows Subsystem for Linux
- Ubuntu
- Linux user account
- Working Linux terminal

---

# Skills Practiced

- Windows administration
- PowerShell
- DISM troubleshooting
- Linux environment setup
- Documentation
- Problem solving

---

# Cybersecurity Relevance

This project helped build skills in:

- Operating system troubleshooting
- Linux administration
- Lab environment setup
- Documentation and reporting
- Investigative thinking
