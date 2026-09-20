# Project 04 – Windows 11 Client

## Overview

This project deploys a Windows 11 client (`WKS-W11-01`) on the VirtualBox platform established in Project 01, joins it to the `jamaursec.lab` domain built in Project 03, and uses it to validate Group Policy processing from a genuine domain-joined machine.

Project 03 relied on a documented lab-only deviation — temporarily granting the `IT` group local-logon rights directly on the domain controller — because no domain-joined client existed yet to test user-scope Group Policy against. This project removes that need entirely and retires the deviation once a real client confirms the same policy applies correctly on its own.

---

## Objectives

- Deploy a Windows 11 Enterprise Evaluation VM in VirtualBox
- Configure EFI, TPM 2.0, and Secure Boot to meet Windows 11 requirements
- Configure static DNS pointing at the domain controller
- Join the client to the `jamaursec.lab` domain
- Verify domain authentication from the client
- Verify Group Policy (`Restrict Control Panel`) applies correctly from a real client
- Confirm the client's computer object in Active Directory
- Retire the Project 03 DC local-logon lab deviation

---

## Technologies Used

### Virtualization

- VirtualBox 7.2.6

### Operating System

- Windows 11 Enterprise Evaluation

### Windows Components

- System Properties (domain join, computer rename)
- Network & Internet settings (static DNS)
- PowerShell

### Active Directory / Group Policy

- Active Directory Users and Computers (`SRV-DC01`)
- Group Policy Management (`SRV-DC01`)
- `gpresult`

---

## Client Configuration

| Setting | Value |
|---------|-------|
| VM Name | `WKS-W11-01` |
| Base Memory | 4096 MB |
| Processors | 2 |
| Firmware | EFI, TPM 2.0, Secure Boot enabled |
| Disk | 64 GB VDI, SATA, dynamically allocated |
| Network | NAT Network `jamaursec-nat` |
| Operating System | Windows 11 Enterprise Evaluation |
| Windows Computer Name | `WKS-W11-01` (renamed from auto-generated `DESKTOP-UM40F7A`) |
| Static DNS | `192.168.45.129` (`SRV-DC01`) |
| Domain | `jamaursec.lab` |

---

## Project Walkthrough

### 1. Created the VM

Built `WKS-W11-01` in VirtualBox with 4096 MB RAM, 2 CPUs, EFI firmware, TPM 2.0, Secure Boot, and a 64 GB SATA disk, attached to the shared `jamaursec-nat` NAT Network so it can reach `SRV-DC01`.

---

### 2. Installed Windows 11 Enterprise Evaluation

Booted the Enterprise Evaluation ISO, selected a clean install ("Keep nothing"), and completed OOBE offline (no internet detected during setup), which led directly into local account creation — a local administrator account (`localadmin`) used to later perform the domain join.

---

### 3. Configured Static DNS

Set the client's Ethernet adapter to use `192.168.45.129` (`SRV-DC01`) as its Preferred DNS server, replacing DHCP-assigned DNS — a required prerequisite for resolving and joining an Active Directory domain.

---

### 4. Joined the Domain

Verified connectivity to `SRV-DC01` (`ping`), then joined `WKS-W11-01` to `jamaursec.lab` via System Properties, authenticating with domain credentials. Confirmed the "Welcome to the jamaursec.lab domain" dialog and restarted.

---

### 5. Renamed the Client

Renamed the Windows computer name from the auto-generated `DESKTOP-UM40F7A` to `WKS-W11-01`, matching the VM name and the project's hostname convention (consistent with `SRV-DC01` in Project 02). This required a second restart.

---

### 6. Verified Domain Login and Group Policy

Logged in as the domain user `JAMAURSEC\jdoe` and ran `gpresult /R /SCOPE USER`, confirming Group Policy was applied from `SRV-DC01.jamaursec.lab` and that the `Restrict Control Panel` GPO from Project 03 was in the Applied Group Policy Objects list, with Local Group Policy correctly filtered out. Confirmed the restriction visually by attempting to open Control Panel and receiving the expected block dialog.

---

### 7. Confirmed the Computer Object in Active Directory

Reviewed Active Directory Users and Computers on `SRV-DC01` and confirmed `WKS-W11-01` registered as a computer object under the default `Computers` container.

---

### 8. Retired the Project 03 Lab Deviation

Removed the `IT` group from **Allow log on locally** on the Default Domain Controllers Policy, ran `gpupdate /force` on `SRV-DC01`, and re-tested a local logon attempt as `jdoe` directly on the domain controller — correctly blocked again, confirming the domain controller is back to its production-realistic default and no longer needs the lab-only exception.

---

## Screenshots

| Screenshot | Description |
|------------|-------------|
| `project-04-windows-11-client-vm-created` | VirtualBox Details pane confirming hardware and firmware configuration |
| `project-04-windows-11-client-installation` | Windows 11 Setup "Ready to install" screen |
| `project-04-windows-11-client-first-login` | Desktop after first local sign-in |
| `project-04-windows-11-client-system-info` | `systeminfo` confirming Windows 11 Enterprise Evaluation |
| `project-04-windows-11-client-dns-configured` | IPv4 Properties showing static DNS `192.168.45.129` |
| `project-04-windows-11-client-domain-join` | "Welcome to the jamaursec.lab domain" success dialog |
| `project-04-windows-11-client-gpresult-user` | `gpresult /R /SCOPE USER` showing Group Policy applied from `SRV-DC01.jamaursec.lab` |
| `project-04-windows-11-client-control-panel-restricted` | Control Panel blocked on screen for domain user `jdoe` |
| `project-04-windows-11-client-ad-computer-object` | `WKS-W11-01` computer object in Active Directory Users and Computers |

**Note:** a dedicated "domain login" screenshot was planned but not captured as a separate file — the `gpresult` screenshot above covers the same verification (domain identity, hostname, and GPO source) more thoroughly. See `project-notes.md` for details.

---

## Challenges Encountered

### VM Name Collision on Creation

The "New Virtual Machine" wizard refused to accept the name `WKS-W11-01` (persistent red validation outline, Finish greyed out) because a leftover, empty `WKS-W11-01` folder already existed under `~/VirtualBox VMs/` from an earlier, cancelled attempt.

**Resolution:** confirmed the folder was empty via `ls -la`, then removed it with `rm -rf` before recreating the VM.

---

### "No Internet" During OOBE Network Setup

Despite being attached to the `jamaursec-nat` NAT Network, Windows Setup reported "No Internet" on the network-connection screen during OOBE.

**Resolution:** selected "I don't have internet," which proceeded directly to local account creation — the desired path anyway, since a local administrator account was needed to perform the domain join.

---

### Initial Ping Failures to the Domain Controller

The first attempts to reach `SRV-DC01` by both hostname and IP address failed (`ping request could not find host` / request timed out), because `SRV-DC01` had not yet been started and was still booting.

**Resolution:** started `SRV-DC01` and waited for it to fully boot; subsequent pings succeeded with 0% packet loss.

---

### Windows Computer Name vs. VirtualBox VM Name

The VM was named `WKS-W11-01` in VirtualBox from creation, but the actual Windows installation still reported its auto-generated name, `DESKTOP-UM40F7A` — VirtualBox's VM name has no effect on the guest OS's hostname.

**Resolution:** manually renamed the computer via System Properties after the domain join, which required an additional restart.

---

## Lessons Learned

- The VirtualBox VM name and the guest OS's computer name are independent — renaming one does not rename the other.
- A "No Internet" network status during Windows Setup doesn't necessarily indicate a broken virtual network; it can still lead into a usable, even preferable, setup path.
- Before troubleshooting client-side DNS or firewall issues, confirm the target server is actually powered on and fully booted.
- Leftover VM folders from a cancelled wizard attempt will block reuse of that VM name until manually removed.
- Validating Group Policy from a genuine domain-joined client is a stronger, more representative test than a temporary local-logon exception on the domain controller — and removing that exception once a real client exists restores the DC to a realistic security posture.

---

## Project Outcome

Successfully deployed a Windows 11 Enterprise Evaluation client, joined it to `jamaursec.lab`, and confirmed Group Policy enforcement from a real domain-joined machine.

Completed tasks include:

- Windows 11 client VM deployment with EFI, TPM 2.0, and Secure Boot
- Static DNS configuration
- Domain join and computer rename
- Domain authentication verification
- Group Policy verification (`gpresult` + visual confirmation)
- Active Directory computer object confirmation
- Retirement of the Project 03 DC local-logon lab deviation

---

## Project Structure

```text
Project-04-Windows-11-Client/
├── README.md
├── architecture.md
├── project-notes.md
└── images/
    ├── project-04-windows-11-client-vm-created.png
    ├── project-04-windows-11-client-installation.png
    ├── project-04-windows-11-client-first-login.png
    ├── project-04-windows-11-client-system-info.png
    ├── project-04-windows-11-client-dns-configured.png
    ├── project-04-windows-11-client-domain-join.png
    ├── project-04-windows-11-client-gpresult-user.png
    ├── project-04-windows-11-client-control-panel-restricted.png
    └── project-04-windows-11-client-ad-computer-object.png
```

---

## Related Documentation

- `project-notes.md` – Detailed build notes, commands, verification, and troubleshooting
- `architecture.md` – Client, network, and domain-join architecture and design decisions

---

## Next Project

**Project 05 – File Services**

The next phase builds enterprise file services on top of the now-validated Active Directory and client infrastructure.

---

## Author

**Ja'Maurian Williams**

Home Lab Series

Project 04 – Windows 11 Client
