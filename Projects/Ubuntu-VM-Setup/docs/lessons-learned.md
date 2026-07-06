# WSL Migration and Troubleshooting

## Situation

Both Ubuntu and Xubuntu virtual machines experienced installation problems and crashes inside VirtualBox.

To continue learning Linux and cybersecurity concepts, I decided to use Windows Subsystem for Linux (WSL).

---

## Initial Problems

### Ubuntu and Xubuntu VM Issues

Problems encountered:

- Ubuntu installer freezes
- Loading spinner hangs
- Display driver issues
- Xubuntu installation problems
- Virtual machine crashes

Troubleshooting attempted:

- Safe graphics mode
- Display settings adjustments
- Increased video memory
- Multiple reinstall attempts

---

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

## Investigation

Commands:

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

## Resolution

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

## Installation Delay

The installation appeared frozen at:

```text
Installing: Ubuntu
49.1%
```

After pressing `Ctrl + C`, the installation immediately completed successfully.

Output:

```text
Distribution successfully installed.
Launching Ubuntu...
```

---

## Lessons Learned

- Terminal output can sometimes be misleading.
- Not every installation delay is a failure.
- Gather information before assuming something is broken.
- Documentation makes troubleshooting easier.
- WSL provides a lightweight Linux environment without requiring a virtual machine.

---

## Skills Practiced

- Troubleshooting
- PowerShell
- DISM commands
- Linux environment setup
- Documentation
- Problem solving