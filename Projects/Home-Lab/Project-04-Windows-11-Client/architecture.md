# Project 04 – Windows 11 Client Architecture

## Overview

Project 04 adds a Windows 11 Enterprise Evaluation client, `WKS-W11-01`, to the `jamaursec.lab` domain established in Project 03, on the VirtualBox platform built in Project 01 and the domain controller (`SRV-DC01`) built in Project 02.

Its purpose is architectural as much as functional: it closes the loop between Active Directory's identity/policy layer and an actual client machine, so Group Policy can be validated the way it would be in a real environment rather than through the domain controller's own local console.

---

# Lab Environment

## Host System

- Ubuntu 26.04.1 LTS
- VirtualBox 7.2.6

---

## Virtual Machines

### Domain Controller

| Component | Configuration |
|-----------|---------------|
| Hostname | `SRV-DC01` |
| Operating System | Windows Server 2022 |
| Role | Primary Domain Controller |
| IPv4 Address | 192.168.45.129 |

### Client

| Component | Configuration |
|-----------|---------------|
| Hostname | `WKS-W11-01` |
| Operating System | Windows 11 Enterprise Evaluation |
| Role | Domain-joined workstation |
| Base Memory | 4096 MB |
| Processors | 2 |
| Firmware | EFI, TPM 2.0, Secure Boot |
| Disk | 64 GB VDI (SATA, dynamically allocated) |
| DNS | Static — `192.168.45.129` |
| Domain | `jamaursec.lab` |

---

# Network Configuration

Both `SRV-DC01` and `WKS-W11-01` share the same VirtualBox NAT Network:

```
NAT Network: jamaursec-nat
Subnet:      192.168.45.0/24
Gateway:     192.168.45.1
```

`WKS-W11-01`'s DNS is statically configured to point at `SRV-DC01` (`192.168.45.129`) rather than relying on DHCP-assigned DNS from the NAT Network — Active Directory domain resolution requires the client to query the domain controller's DNS directly.

---

# Logical Architecture

```text
                 VirtualBox 7.2.6 (Ubuntu Host)
                             │
                    NAT Network: jamaursec-nat
                             │
          ┌──────────────────┴──────────────────┐
          │                                     │
   Windows Server 2022                   Windows 11 Enterprise
       SRV-DC01                            WKS-W11-01
   (Domain Controller)                  (Domain-Joined Client)
          │                                     │
   Active Directory                     Static DNS → SRV-DC01
   Domain: jamaursec.lab                        │
          │                            Domain Join: jamaursec.lab
   Group Policy Objects                          │
     (Restrict Control Panel)  ──────────►  Policy Applied
                                          (verified via gpresult)
```

---

# Domain Join Workflow

```text
Static DNS configured (client → SRV-DC01)
              │
              ▼
   Connectivity verified (ping)
              │
              ▼
  System Properties → Change → Domain
              │
              ▼
   Domain credentials authenticated
              │
              ▼
  "Welcome to the jamaursec.lab domain"
              │
              ▼
          Restart
              │
              ▼
  Computer renamed (DESKTOP-* → WKS-W11-01)
              │
              ▼
          Restart
              │
              ▼
   Domain login as JAMAURSEC\jdoe
```

---

# Group Policy Validation Architecture

Project 03 could only verify the `Restrict Control Panel` GPO's user-scope behavior through a temporary, documented lab-only exception: granting the `IT` group **Allow log on locally** directly on the domain controller, since no domain-joined client existed.

Project 04 replaces that verification path entirely:

```text
Project 03 (temporary)                Project 04 (real validation)
──────────────────────                ──────────────────────────
IT group granted local logon    →     Real client (WKS-W11-01)
on SRV-DC01 itself                    joined to the domain

jdoe logs on directly to the DC →     jdoe logs on to WKS-W11-01

gpresult run on the DC          →     gpresult run on the client,
                                       policy sourced from SRV-DC01
```

Once Project 04 confirmed the GPO applies correctly from `WKS-W11-01`, the Project 03 exception was removed from the Default Domain Controllers Policy and `SRV-DC01` was re-verified to block domain-user local logon again — restoring the domain controller to a production-realistic default.

---

# Validation Performed

Verified:

- VM hardware and firmware configuration prior to installation (EFI, TPM 2.0, Secure Boot)
- Windows 11 Enterprise Evaluation installed (`systeminfo`)
- Static DNS configured and functioning
- Connectivity to the domain controller
- Successful domain join and computer rename
- Domain authentication as `jdoe`
- `Restrict Control Panel` GPO applied from the client, sourced from `SRV-DC01.jamaursec.lab`
- Control Panel restriction enforced on screen
- `WKS-W11-01` computer object present in Active Directory
- Project 03 DC local-logon deviation removed and re-verified as blocked

---

# Design Decisions

- **Static DNS on the client, not DHCP-provided DNS** — the NAT Network's default DHCP does not point clients at the domain controller's DNS automatically; a real enterprise client would typically receive this via DHCP scope options, but a manual static entry keeps the lab's dependency explicit and visible.
- **Client joined directly rather than pre-staged into an OU** — `WKS-W11-01` lands in the default `Computers` container after a self-service domain join, matching how most real-world domain joins actually behave unless a computer object is deliberately pre-created in a target OU.
- **Computer renamed after, not during, installation** — Windows Setup's OOBE doesn't prompt for a custom computer name in this build, so the rename is a deliberate post-install step to align the hostname with the project's naming convention, consistent with the `SRV-DC01` rename in Project 02.
- **Verification performed from the client, not the DC** — replacing the Project 03 workaround with genuine client-side verification is the entire point of this project; it's a stronger and more representative test of the Group Policy design than console access to the domain controller itself.

---

# Future Expansion

`WKS-W11-01` now serves as the Home Lab's first real client machine, providing a foundation for:

- Enterprise File Services (Project 05) — mapped drives, share permissions tested from a genuine client
- Additional Group Policy Objects (software restriction, drive mapping, desktop configuration)
- DHCP — replacing the client's static DNS/IP configuration with a scope-delivered configuration
- osTicket Help Desk
- pfSense Firewall
- SIEM Integration
- PowerShell automation
- Enterprise troubleshooting scenarios involving a real client-to-DC relationship

---

# Skills Demonstrated

- Windows 11 client deployment (EFI, TPM 2.0, Secure Boot)
- Static DNS configuration for Active Directory name resolution
- Domain join and computer rename workflows
- Group Policy verification from a real client (`gpresult`)
- Active Directory computer object administration
- Security posture restoration (retiring a temporary lab exception)
- Enterprise infrastructure validation methodology
