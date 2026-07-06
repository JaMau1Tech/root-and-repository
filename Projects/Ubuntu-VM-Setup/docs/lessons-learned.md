# WSL Migration and Troubleshooting

## Project Overview

Both Ubuntu and Xubuntu virtual machines experienced installation problems and instability inside Oracle VirtualBox.

To continue learning Linux and cybersecurity concepts without further delays, I decided to migrate to Windows Subsystem for Linux (WSL).

---

# Objective

Create a stable Linux environment for:

- Learning Linux fundamentals
- Practicing command-line skills
- Running development tools
- Building cybersecurity knowledge
- Continuing hands-on learning without relying on virtual machines

---

# Initial Virtual Machine Problems

## Ubuntu and Xubuntu Issues

Problems encountered:

- Ubuntu installer freezes
- Loading spinner hangs indefinitely
- Display driver compatibility issues
- Xubuntu installation problems
- Virtual machine crashes and instability

---

# Troubleshooting Attempted

- Booted using Safe Graphics Mode
- Adjusted VirtualBox display settings
- Increased video memory
- Reinstalled operating systems multiple times
- Modified VM hardware configurations

Although some improvements were made, the environment remained unstable.

---

# Decision to Migrate to WSL

Because the virtual machines continued to experience problems, I decided to use:

```text
Windows Subsystem for Linux (WSL)
```

Benefits:

- Lightweight
- Faster startup times
- Lower resource usage
- Easy integration with Windows
- Excellent for Linux learning and development

---

# WSL Installation Problems

## WSL1 Not Supported

Command:

```powershell
wsl --status
```

Output:

```text
Default Version: 2
WSL1 is not supported with your current machine configuration.
```

---

## Windows Feature Error

Command:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

Output:

```text
Feature name Microsoft-Windows-Subsystem-Linux is unknown.
```

---

# Investigation

Commands used:

```powershell
DISM /Online /Get-Features /Format:Table | findstr /i "linux"

DISM /Online /Get-Features /Format:Table | findstr /i "virtual"
```

Findings:

```text
Microsoft-Windows-Subsystem-Linux | Disabled
VirtualMachinePlatform | Enabled
```

---

# Resolution

Restarted the computer.

After reboot:

```powershell
wsl --status
```

Output:

```text
Default Version: 2
```

Installed Ubuntu:

```powershell
wsl --install
```

---

# Installation Delay

The installation appeared frozen at:

```text
Installing: Ubuntu
49.1%
```

After pressing:

```text
Ctrl + C
```

the installation immediately completed successfully.

Output:

```text
Distribution successfully installed.
Launching Ubuntu...
```

---

# Final Result

Successfully installed:

- Windows Subsystem for Linux (WSL)
- Ubuntu
- Linux user account
- Working Linux terminal

Successfully launched:

```text
jamaurlan@DESKTOP-XXXXX:~$
```

The system was now ready for:

- Linux command-line practice
- Python development
- Git and GitHub workflows
- Cybersecurity learning and experimentation

---

# Lessons Learned

- Terminal output can sometimes be misleading.
- Not every installation delay indicates failure.
- Gather information before assuming something is broken.
- Troubleshooting often requires multiple approaches.
- Documentation makes future troubleshooting significantly easier.
- WSL provides an excellent lightweight Linux environment.

---

# Skills Practiced

- Troubleshooting
- Problem solving
- PowerShell
- DISM commands
- Windows administration
- Linux environment setup
- Documentation
- Research and investigation

---

# Cybersecurity Relevance

This project helped build skills that are directly applicable to cybersecurity:

- Operating system troubleshooting
- Linux administration
- Documentation and reporting
- Investigative thinking
- Understanding virtualization technologies
- Building and maintaining lab environments

---

# Future Goals

- Learn Linux fundamentals.
- Practice Bash commands.
- Learn package management.
- Use WSL for Python development.
- Build additional cybersecurity labs using Linux.
- Continue documenting all projects and lessons learned.