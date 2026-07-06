# Xubuntu Loading Spinner Issue

## Problem

The virtual machine became stuck on the Xubuntu loading spinner during startup.

The operating system failed to continue booting into the desktop environment.

---

# Symptoms

The following behavior was observed:

- Loading spinner remained on screen indefinitely.
- Desktop environment failed to load.
- System appeared frozen.
- Installation could not continue normally.

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

# Troubleshooting Steps

## Step 1 – Restarted the Virtual Machine

Rebooted the virtual machine and attempted to boot again.

Result:

```text
Issue persisted.
```

---

## Step 2 – Verified ISO Integrity

Confirmed that the installation media was downloaded correctly and was not corrupted.

Result:

```text
ISO file was valid.
```

---

## Step 3 – Adjusted Display Settings

Reviewed and modified:

- Graphics controller settings
- Display configuration
- Video memory allocation

Result:

```text
Issue persisted.
```

---

## Step 4 – Used Safe Graphics Mode

Booted the operating system using:

```text
Ubuntu (Safe Graphics)
```

Result:

```text
System booted successfully.
Desktop environment loaded correctly.
Installation completed successfully.
```

---

# Root Cause

The issue appeared to be related to:

- Graphics compatibility
- Display driver initialization
- VirtualBox display configuration

Safe Graphics Mode bypassed the graphical issues and allowed the operating system to load properly.

---

# Outcome

Successfully booted into the Xubuntu desktop environment and completed the installation.

The virtual machine became fully operational.

---

# Lessons Learned

- A loading spinner does not always indicate a permanent system failure.
- Safe Graphics Mode is a useful troubleshooting option when Linux experiences display problems.
- Troubleshooting often requires testing multiple solutions before finding the correct fix.
- Documenting issues and solutions makes future troubleshooting significantly easier.

---

# Skills Practiced

- Troubleshooting
- Virtualization
- Problem solving
- Linux installation
- Documentation
- Research and investigation

---

# Cybersecurity Relevance

Cybersecurity professionals regularly troubleshoot:

- Operating system failures
- Software installation issues
- Virtual machine problems
- Configuration errors

Developing a structured troubleshooting process is an essential skill in both IT and cybersecurity.

---

# Future Improvements

- Create VirtualBox snapshots before major changes.
- Test additional display configurations.
- Build additional Linux virtual machines for practice.
- Continue documenting all issues and resolutions.