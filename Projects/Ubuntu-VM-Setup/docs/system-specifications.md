# System Specifications

This document records the hardware and software configuration used for the Ubuntu Virtual Machine project.

---

# Host System

## Operating System

```text
Windows 11
```

## Purpose

The host operating system used to run Oracle VirtualBox and manage the Linux virtual machine environment.

---

# Virtualization Platform

## Software

```text
Oracle VirtualBox
```

## Purpose

Provides the ability to create and manage virtual machines for learning Linux, networking, and cybersecurity concepts.

---

# Guest Operating System

## Distribution

```text
Xubuntu 26.04
```

## Purpose

A lightweight Linux distribution selected for:

- Linux command-line practice
- System administration exercises
- Cybersecurity labs
- Resource efficiency

---

# Virtual Machine Hardware Allocation

## Memory (RAM)

```text
2048 MB
```

Reason:

Provides enough memory to run Xubuntu while leaving resources available for the Windows host system.

---

## Processor

```text
1 CPU Core
```

Reason:

Sufficient for:

- Linux fundamentals
- Command-line practice
- Documentation work
- Introductory cybersecurity labs

---

## Storage

```text
25 GB Virtual Disk
```

Reason:

Provides adequate space for:

- Operating system installation
- Software updates
- Project documentation
- Screenshots
- Learning tools

---

## Video Memory

```text
128 MB
```

Reason:

Provides improved graphical performance and desktop compatibility.

---

## Network Configuration

```text
NAT Adapter
```

Reason:

Allows the virtual machine to:

- Access the internet
- Download updates
- Install software
- Remain isolated from the local network

---

# Environment Purpose

This virtual machine was created to provide a safe environment for:

- Learning Linux
- Practicing troubleshooting
- Experimenting with cybersecurity tools
- Building documentation habits
- Developing hands-on technical skills

---

# Lessons Learned

- Resource allocation directly impacts virtual machine performance.
- Lightweight Linux distributions perform well on limited hardware.
- Documenting configurations makes troubleshooting and rebuilding environments significantly easier.
- Understanding system specifications is an important skill in both IT and cybersecurity.

---

# Future Improvements

- Increase RAM to 4096 MB if additional tools are installed.
- Experiment with Bridged Networking.
- Create additional virtual machines for cybersecurity labs.
- Build a dedicated penetration testing environment.