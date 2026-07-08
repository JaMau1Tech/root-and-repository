# WSL Feature Name Unknown Error

## Problem

Attempted to manually enable WSL using:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

Received:

```text
Feature name Microsoft-Windows-Subsystem-Linux is unknown.
```

---

# Investigation

Checked available Windows features:

```powershell
DISM /Online /Get-Features /Format:Table | findstr /i "linux"
```

Result:

```text
Microsoft-Windows-Subsystem-Linux | Disabled
```

This showed that the feature existed even though the earlier command returned an error.

---

# Resolution

Restarted Windows and re-ran:

```powershell
wsl --status
```

The system recognized WSL correctly after restart.

---

# Root Cause

The issue appeared to be caused by Windows not fully recognizing the WSL feature state until after a restart.

---

# Lessons Learned

- Error messages can be misleading.
- Verify system state with multiple commands.
- Restarting Windows can resolve feature-detection issues.
- Documentation helps preserve troubleshooting steps.
