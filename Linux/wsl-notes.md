# WSL Notes

## What is WSL?

Windows Subsystem for Linux allows Linux distributions to run directly inside Windows without requiring a full virtual machine.

---

# Benefits

- Lightweight
- Faster than a virtual machine
- Useful for command-line practice
- Good for scripting and development
- Easy access to Linux tools inside Windows

---

# Installation Steps

1. Open PowerShell as Administrator.
2. Check WSL status:

```powershell
wsl --status
```

3. Install WSL and Ubuntu:

```powershell
wsl --install
```

4. Restart the computer if prompted.
5. Launch Ubuntu.
6. Create a Linux username and password.

---

# First Successful Login

Reached the Linux shell:

```text
jamaur1an@DESKTOP-RR8P5KS:~$
```

This confirmed:

- Ubuntu installed successfully
- Linux user account was created
- WSL environment was operational

---

# Commands Practiced

```bash
whoami
pwd
ls
```

---

# Lessons Learned

- WSL is useful for Linux practice on Windows.
- Closing the terminal does not delete the WSL environment.
- The Linux prompt confirms the environment is ready.
- Terminal output may appear frozen even when installation is still progressing.
