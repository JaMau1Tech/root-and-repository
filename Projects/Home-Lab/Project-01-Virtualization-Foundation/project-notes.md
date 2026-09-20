# Project 01 – Virtualization Foundation

## Status

✅ Completed

---

# Overview

This project establishes the virtualization foundation for the Home Lab on a new host, after the original host (Windows 11 Home, VMware Workstation Pro, Ubuntu 24.04.4 LTS VM) was reinstalled and replaced.

Instead of hosting the lab's Linux system as a VM inside another hypervisor, this build runs Ubuntu directly on the host hardware. Ubuntu is both the daily-use operating system and the platform for VirtualBox, which is now the hypervisor for every Home Lab VM going forward (Windows Server, Active Directory, and future projects).

This project establishes the host, its security baseline, the hypervisor, and the lab's virtual network — the foundation every later project builds on.

---

# Objectives

- Install Ubuntu LTS as the host operating system
- Apply a baseline security configuration (firewall, disk encryption, automatic updates, Secure Boot)
- Install VirtualBox as the Home Lab hypervisor
- Resolve Secure Boot's kernel module signing requirement for VirtualBox
- Create the isolated virtual network used by all lab VMs
- Verify the platform is ready to host Windows Server and future guests

---

# Environment

## Host Hardware

- Dell Latitude 5320
- Intel Core i5-1145G7 (4 cores / 8 threads)
- 16 GB RAM
- 512 GB disk

## Host Operating System

- Ubuntu 26.04.1 LTS

## Hypervisor

- VirtualBox 7.2.6

---

# Installation Process

## Host OS Installation

Ubuntu 26.04.1 LTS was installed as a clean install (erase disk), using GPT partitioning and UEFI boot to match the machine's existing firmware mode. The installer USB was created with Rufus, using the GPT partition scheme and UEFI (non-CSM) target.

Disk encryption (LUKS) was enabled during installation.

---

# Security Baseline

A short hardening pass was completed immediately after the OS install, before any lab work began:

| Control | Configuration | Verified With |
|---|---|---|
| Firewall | `ufw` enabled, default deny incoming | `sudo ufw status verbose` |
| Disk encryption | LUKS (`crypto_LUKS`), root filesystem inside the encrypted volume | `lsblk -f` |
| Automatic security updates | `unattended-upgrades` enabled | `systemctl is-enabled unattended-upgrades` |
| Secure Boot | Enabled and enforced | `mokutil --sb-state` |

---

# Hypervisor Installation

## VirtualBox

Installed via `apt`:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install virtualbox
```

### Secure Boot / Kernel Module Signing

With Secure Boot enabled, VirtualBox's kernel modules (`vboxdrv` and related) are unsigned by default and will not load until they're enrolled as a trusted key (MOK — Machine Owner Key).

Resolution:

1. During the VirtualBox `dkms` install, a one-time MOK enrollment password was set.
2. On reboot, the blue MOK management screen was used to **Enroll MOK**, entering that password.
3. After the reboot completed, the modules loaded successfully:

```bash
lsmod | grep vbox
```

VirtualBox Manager then opened with no driver error.

---

# Lab Network Configuration

A dedicated NAT Network was created in VirtualBox so every Home Lab VM shares an isolated, addressable network segment rather than the host's own network:

| Setting | Value |
|---|---|
| Network Name | `jamaursec-nat` |
| Network CIDR | 192.168.45.0/24 |
| Gateway | 192.168.45.1 |
| DHCP | Enabled |

This network is what Project 02's server (`SRV-DC01`) and every later Home Lab VM attach to.

---

# Verification

```bash
lscpu | grep Virtualization
```

Verified: `VT-x` present (required before installing a hypervisor).

```bash
sudo ufw status verbose
```

Verified: firewall active, default deny incoming.

```bash
lsblk -f
```

Verified: `crypto_LUKS` present, root filesystem mounted inside the encrypted volume.

```bash
systemctl is-enabled unattended-upgrades
```

Verified: enabled.

```bash
mokutil --sb-state
```

Verified: SecureBoot enabled.

```bash
lsmod | grep vbox
```

Verified: VirtualBox kernel modules loaded.

---

# Challenges Encountered

## Secure Boot Blocking VirtualBox

Issue:

VirtualBox installed successfully via `apt`, but its kernel modules failed to load, since Secure Boot rejects unsigned kernel modules by default.

Resolution:

Completed the MOK enrollment flow (one-time password at install, **Enroll MOK** on the following reboot) so the system trusts VirtualBox's self-signed modules. VirtualBox then started normally.

---

## Lessons Learned

- A hypervisor that installs cleanly can still fail silently at the kernel-module level under Secure Boot — always check `lsmod` before assuming the install worked.
- Ubuntu's security defaults (firewall off, no full-disk encryption unless selected at install, updates not fully automatic) need a deliberate pass right after install, not "later."
- Hosting the hypervisor directly on bare metal, instead of nesting a Linux VM inside another hypervisor, removes a layer of dependency that a wiped host would otherwise take down with it.
- Creating the lab's virtual network (NAT Network) as its own named object, rather than relying on default NAT, keeps every future VM's addressing consistent and documented.

---

# Skills Developed

## Linux Administration

- Ubuntu LTS installation and partitioning (GPT/UEFI)
- System hardening: firewall, disk encryption, automatic updates
- Secure Boot and kernel module signing (MOK enrollment)

## Virtualization

- VirtualBox installation and troubleshooting
- Virtual network design (NAT Network)

## System Administration

- Command-line verification methodology
- Documented, repeatable host setup

---

# Project Outcome

Established a hardened Ubuntu LTS host running VirtualBox as the Home Lab's hypervisor, with a dedicated isolated network (`jamaursec-nat`) ready for guest VMs. This host now underpins:

- Windows Server / Active Directory (Project 02–03)
- Windows 11 domain-joined client (Project 04)
- All future Home Lab infrastructure

---

# Next Project

Project 02 – Windows Server Foundation

Objectives:

- Deploy Windows Server 2022 in VirtualBox
- Configure enterprise server settings
- Install VirtualBox Guest Additions
- Configure a static IP address
- Prepare the server for Active Directory
