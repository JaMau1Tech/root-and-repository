# Project 01 – Virtualization Foundation

## Overview

This project establishes the virtualization foundation for the Home Lab: a hardened Ubuntu LTS host running VirtualBox as the hypervisor, with a dedicated virtual network for lab VMs.

Unlike the lab's earlier iteration, Ubuntu is not run as a guest VM here — it is the host operating system itself, on a Dell Latitude 5320. VirtualBox, installed on top of it, is the hypervisor every later Home Lab project (Windows Server, Active Directory, and beyond) builds its VMs in.

---

## Objectives

- Install Ubuntu LTS as the host operating system
- Apply a security baseline: firewall, disk encryption, automatic updates, Secure Boot
- Install VirtualBox and resolve Secure Boot's kernel module signing requirement
- Create the isolated NAT Network used by all lab VMs
- Verify the platform is ready for Windows Server deployment

---

## Technologies Used

### Host

- Ubuntu 26.04.1 LTS
- Dell Latitude 5320 (Intel Core i5-1145G7, 16 GB RAM, 512 GB disk)

### Hypervisor

- VirtualBox 7.2.6

### Security

- ufw (firewall)
- LUKS (disk encryption)
- unattended-upgrades (automatic security updates)
- Secure Boot with MOK (Machine Owner Key) enrollment

---

## Host & Hypervisor Configuration

| Setting | Value |
|---------|-------|
| Host OS | Ubuntu 26.04.1 LTS |
| Partitioning | GPT / UEFI |
| Disk Encryption | LUKS |
| Firewall | ufw, default deny incoming |
| Automatic Updates | Enabled |
| Secure Boot | Enabled |
| Hypervisor | VirtualBox 7.2.6 |
| Lab Network | NAT Network `jamaursec-nat`, 192.168.45.0/24, gateway 192.168.45.1 |

---

## Project Walkthrough

### 1. Installed Ubuntu 26.04.1 LTS

Clean install (erase disk), GPT partitioning, UEFI boot, disk encryption enabled at install time.

---

### 2. Applied the Security Baseline

Verified and enabled:

- Firewall (`ufw`)
- Disk encryption (LUKS)
- Automatic security updates (`unattended-upgrades`)
- Secure Boot

---

### 3. Installed VirtualBox

Installed via `apt`. Resolved a Secure Boot kernel-module signing issue by completing the MOK enrollment flow, after which VirtualBox's kernel modules loaded successfully.

---

### 4. Created the Lab Network

Built a dedicated VirtualBox NAT Network (`jamaursec-nat`, 192.168.45.0/24) so every Home Lab VM can reach each other and the internet on a consistent, isolated segment.

---

### 5. Verified the Platform

Confirmed CPU virtualization support, firewall status, disk encryption, automatic updates, Secure Boot state, and that VirtualBox's kernel modules were loaded.

---

## Screenshots

No screenshots were captured for this project. The host setup, security baseline, and hypervisor installation were carried out and verified via the command-line output documented in `project-notes.md`.

---

## Challenges Encountered

### Secure Boot Blocking VirtualBox

VirtualBox installed successfully via `apt`, but its kernel modules didn't load because Secure Boot rejects unsigned modules by default.

**Resolution**

Completed the MOK (Machine Owner Key) enrollment flow: set a one-time password during install, then enrolled it on the blue MOK management screen at the next reboot. VirtualBox started normally afterward.

---

## Lessons Learned

- A hypervisor can install without error and still not actually work under Secure Boot — verify the kernel modules loaded, don't just verify the package installed.
- Security defaults (firewall, disk encryption, automatic updates) are not all on by default on a fresh Ubuntu install and are worth checking immediately, before any lab work begins.
- Running the hypervisor on bare metal, rather than nesting the Linux host inside another hypervisor, removes one layer that a wiped machine would otherwise take down with it.
- A dedicated, named virtual network (NAT Network) keeps lab VM addressing consistent and documented, rather than relying on default per-VM NAT.

---

## Project Outcome

Established a hardened Ubuntu 26.04.1 LTS host running VirtualBox 7.2.6, with a dedicated isolated network (`jamaursec-nat`) ready for guest VMs.

Completed tasks include:

- Ubuntu LTS installation
- Security baseline (firewall, encryption, updates, Secure Boot)
- VirtualBox installation and Secure Boot resolution
- Lab NAT Network creation
- Full platform verification

The platform is now ready for Windows Server deployment.

---

## Project Structure

```text
Project-01-Virtualization-Foundation/
├── README.md
├── architecture.md
├── project-notes.md
└── images/            (empty — no screenshots for this project)
```

---

## Related Documentation

- `project-notes.md` – Detailed build notes, commands, verification, and troubleshooting
- `architecture.md` – Host, hypervisor, and network architecture and design decisions

---

## Next Project

**Project 02 – Windows Server Foundation**

The next phase deploys Windows Server 2022 in VirtualBox, laying the foundation for Active Directory.

---

## Author

**Ja'Maurian Williams**

Home Lab Series

Project 01 – Virtualization Foundation
