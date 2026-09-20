# Project 01 – Virtualization Foundation Architecture

## Overview

This project establishes the host platform and hypervisor for the Home Lab. Ubuntu LTS runs directly on the host hardware — there is no separate Ubuntu lab VM — and VirtualBox, installed on top of it, is the hypervisor for every guest VM in the Home Lab from Project 02 onward.

---

# Architecture Objectives

- Provide a hardened, reliable host platform
- Install a working hypervisor with Secure Boot enabled
- Establish an isolated virtual network for lab VMs
- Create a clean, documented baseline for future infrastructure projects

---

# Host System

| Component | Specification |
|----------|---------------|
| Hardware | Dell Latitude 5320 |
| Processor | Intel Core i5-1145G7 (4 cores / 8 threads) |
| Memory | 16 GB RAM |
| Storage | 512 GB disk |
| Operating System | Ubuntu 26.04.1 LTS |
| Disk Encryption | LUKS |
| Firewall | ufw (default deny incoming) |
| Automatic Updates | unattended-upgrades |
| Secure Boot | Enabled |
| Hypervisor | VirtualBox 7.2.6 |

---

# Network Architecture

```text
                    Internet
                        │
                        │
              Home Router / ISP
                        │
                        │
              Ubuntu 26.04.1 LTS Host
              (Dell Latitude 5320)
                        │
              VirtualBox 7.2.6
                        │
          NAT Network: jamaursec-nat
              192.168.45.0/24
              Gateway: 192.168.45.1
                        │
          ┌─────────────┴─────────────┐
          │                           │
     SRV-DC01 (Project 02+)   Future Lab VMs
```

### Network Configuration

- Network Mode: VirtualBox NAT Network (not default NAT — a named, shared network so multiple VMs can reach each other and the DHCP-assigned gateway is consistent)
- Network Name: `jamaursec-nat`
- CIDR: 192.168.45.0/24
- Gateway: 192.168.45.1 (VirtualBox's NAT Network default; differs from the previous host's VMware gateway of 192.168.45.2 — noted here since the domain and DNS records built in later projects reference the gateway)
- Internet Access: Verified from the host and from guest VMs

---

# Software Stack

## Host

- Ubuntu 26.04.1 LTS
- VirtualBox 7.2.6
- ufw, unattended-upgrades (security baseline)

## Guests (established in later projects)

- Windows Server 2022 (Project 02–03)
- Windows 11 (Project 04, planned)

---

# Design Decisions

## Ubuntu as the Host OS (no nested Ubuntu VM)

Earlier iterations of this lab ran Ubuntu as a guest VM inside VMware Workstation Pro, on a Windows 11 Home host. This build runs Ubuntu directly on the hardware instead.

### Rationale

- Removes a layer of virtualization overhead for the host OS itself
- The host is already the machine used for documentation and Git work, so one hardened Linux install serves both purposes
- One less thing lost if the host ever needs to be wiped again

## VirtualBox as the Hypervisor

### Rationale

- Runs natively on Linux with first-party packaging (`apt install virtualbox`)
- Free and actively maintained
- Supports NAT Networks, snapshots, and Guest Additions comparable to the previous VMware-based workflow

### Secure Boot Consideration

VirtualBox's kernel modules are unsigned by default and require a one-time MOK (Machine Owner Key) enrollment to load under Secure Boot. This was completed during setup; see project-notes.md for the exact steps.

## NAT Network over Default NAT

A named NAT Network (`jamaursec-nat`) was created instead of relying on VirtualBox's default per-VM NAT, because a shared, isolated network is required for VMs (e.g., a domain controller and its clients) to communicate with each other, not just with the internet.

---

# Baseline Validation

The following checks were completed and verified:

- Ubuntu installation (GPT/UEFI)
- Firewall active (ufw, deny incoming)
- Disk encryption active (LUKS)
- Automatic security updates enabled
- Secure Boot enabled and enforced
- VirtualBox installed and kernel modules loaded (Secure Boot MOK enrollment)
- NAT Network created and reachable
- CPU virtualization extensions (VT-x) present

---

# Recovery Strategy

The host itself is not snapshotted (it is bare-metal Ubuntu). Recovery for this layer is the documented installation and hardening process in project-notes.md, which can be repeated on a replacement host if needed. Guest VM recovery (snapshots) begins with Project 02.

---

# Future Expansion

This host and hypervisor will support the following planned projects:

- Project 02 – Windows Server Foundation
- Project 03 – Active Directory
- Project 04 – Windows 11 Client
- Project 05 – File Services
- Project 06 – Security Hardening
- Project 07 – Monitoring & Logging
- Project 08 – osTicket Help Desk
- Project 09 – pfSense Firewall
- Project 10 – SIEM

---

# Architecture Summary

This project establishes a hardened Ubuntu 26.04.1 LTS host running VirtualBox as the Home Lab's hypervisor, with a dedicated, isolated virtual network (`jamaursec-nat`) for guest VMs. Running the hypervisor directly on the host, rather than nesting it inside another virtualization layer, simplifies the platform and removes a point of failure that contributed to losing the lab environment previously.
