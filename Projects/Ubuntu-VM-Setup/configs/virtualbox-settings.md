# VirtualBox Configuration

This document records the VirtualBox configuration used during the Ubuntu/Xubuntu virtual machine setup.

---

# Virtual Machine Information

## Virtual Machine Name

```text
Cyber-Lab-Ubuntu
```

## Guest Operating System

```text
Xubuntu
```

---

# Hardware Configuration

## Memory

```text
2048 MB
```

Reason:

Allocated enough memory for basic Linux use while leaving resources available for the Windows host.

## Processor

```text
1 CPU Core
```

Reason:

Sufficient for Linux fundamentals, command-line practice, and introductory cybersecurity labs.

## Virtual Hard Disk

```text
25 GB
```

Reason:

Provides space for the operating system, updates, notes, screenshots, and future tools.

---

# Display Configuration

## Graphics Controller

```text
VBoxSVGA
```

## Video Memory

```text
128 MB
```

Reason:

Improves graphical performance and compatibility during installation.

---

# Network Configuration

## Adapter Type

```text
NAT
```

Reason:

Allows the virtual machine to access the internet through the host while keeping it isolated from the local network.

---

# Future Improvements

- Increase RAM to 4096 MB if additional tools are installed.
- Experiment with Bridged Networking.
- Create VirtualBox snapshots before major changes.
- Build additional Linux virtual machines for lab practice.
