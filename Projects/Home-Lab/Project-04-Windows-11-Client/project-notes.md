# Project 04 – Windows 11 Client

## Status

✅ Completed

---

# Overview

This project deployed a Windows 11 Enterprise Evaluation client, `WKS-W11-01`, on the VirtualBox platform established in Project 01, and joined it to the `jamaursec.lab` domain built in Project 03.

Its primary purpose was to validate Group Policy processing from a genuine domain-joined client, replacing the lab-only workaround used in Project 03 (temporarily allowing the `IT` group to log on locally to the domain controller itself, since no domain-joined client existed yet).

---

# Objectives

- Deploy a Windows 11 Enterprise Evaluation VM in VirtualBox
- Configure EFI, TPM 2.0, and Secure Boot
- Configure static DNS pointing at `SRV-DC01`
- Join `WKS-W11-01` to the `jamaursec.lab` domain
- Rename the client to match the project's hostname convention
- Verify domain authentication
- Verify the `Restrict Control Panel` GPO applies from a real client
- Confirm the client's computer object in Active Directory
- Retire the Project 03 DC local-logon lab deviation

---

# Requirements

## Hardware

- Dell Latitude 5320 host

## Hypervisor

- VirtualBox 7.2.6 (see [[Project 01 – Virtualization Foundation]])

## Virtual Machines

- `SRV-DC01` — Windows Server 2022, Domain Controller (see [[Project 02 – Windows Server Foundation]], [[Project 03 – Active Directory]])
- `WKS-W11-01` — Windows 11 Enterprise Evaluation client (this project)

## Software

- Windows 11 Enterprise Evaluation (Microsoft Evaluation Center ISO)
- PowerShell
- Active Directory Users and Computers
- Group Policy Management

---

# Installation

## VM Creation

Created `WKS-W11-01` in VirtualBox:

| Setting | Value |
|---------|-------|
| Base Memory | 4096 MB |
| Processors | 2 |
| EFI | Enabled |
| TPM Type | 2.0 |
| Secure Boot | Enabled |
| Storage | 64.00 GB VDI, SATA, dynamically allocated |
| Network Adapter 1 | Intel PRO/1000 MT Desktop, NAT Network `jamaursec-nat` |

---

## Windows 11 Installation

- Booted the Enterprise Evaluation ISO
- Confirmed edition: Windows 11 Enterprise Evaluation
- Selected clean install ("Keep nothing")
- OOBE reported "No Internet" on the network-connection screen; proceeded via "I don't have internet"
- Created local account `localadmin` (intended for performing the domain join)
- Reached the desktop; initial build watermark read "Windows License is expired" (the downloaded Enterprise Evaluation ISO build is dated March 2024) — did not affect functionality

Post-install verification (PowerShell):

```powershell
systeminfo
```

Result (relevant fields):

```
Host Name:                WKS-W11-01
OS Name:                   Microsoft Windows 11 Enterprise Evaluation
OS Version:                10.0.26200 N/A Build 26200
OS Configuration:          Member Workstation
Registered Owner:          localadmin
System Manufacturer:       innotek GmbH
System Model:              VirtualBox
```

---

## Static DNS Configuration

Set the client's Ethernet adapter (Intel(R) PRO/1000 MT Desktop Adapter) to use a manual DNS server instead of DHCP-assigned DNS:

- Preferred DNS server: `192.168.45.129` (`SRV-DC01`)

This is a required prerequisite for resolving and joining an Active Directory domain — the VirtualBox NAT Network's default DHCP does not supply the domain controller's DNS automatically.

---

## Domain Join

Verified connectivity to `SRV-DC01` before attempting the join:

```powershell
ping SRV-DC01.jamaursec.lab
ping 192.168.45.129
```

Initial attempts failed (see Troubleshooting below); once `SRV-DC01` was confirmed running and fully booted, both name resolution and raw connectivity succeeded with 0% packet loss.

Joined the domain via System Properties → Change:

- Member of: **Domain**, `jamaursec.lab`
- Authenticated with domain credentials
- Confirmed the "Welcome to the jamaursec.lab domain" dialog
- Restarted

---

## Computer Rename

The Windows computer name remained the auto-generated `DESKTOP-UM40F7A` through the domain join — the VirtualBox VM name (`WKS-W11-01`) has no effect on the guest OS's own hostname.

Renamed via System Properties → Change:

- Computer name: `WKS-W11-01`
- Restarted a second time to apply

---

# Configuration

## Domain Login Verification

Logged in as the domain user `JAMAURSEC\jdoe`.

```powershell
gpresult /R /SCOPE USER
```

Result (relevant fields):

```
RSOP data for JAMAURSEC\jdoe on WKS-W11-01 : Logging Mode

OS Configuration:              Member Workstation
OS Version:                    10.0.26200
Local Profile:                 C:\Users\jdoe

USER SETTINGS
    CN=John Doe,OU=IT,DC=jamaursec,DC=lab
    Last time Group Policy was applied:    9/19/2026 at 8:26:43 PM
    Group Policy was applied from:         SRV-DC01.jamaursec.lab
    Domain Name:                           JAMAURSEC
    Domain Type:                           Windows 2008 or later

    Applied Group Policy Objects
    -----------------------------
        Restrict Control Panel

    The following GPOs were not applied because they were filtered out
    ---------------------------------------------------------------------
        Local Group Policy
```

Confirmed visually by attempting to open Control Panel as `jdoe`:

```
This operation has been cancelled due to restrictions in effect on this computer. Please contact your system administrator.
```

---

## Active Directory Computer Object

On `SRV-DC01`, opened Active Directory Users and Computers and confirmed `WKS-W11-01` registered as a `Computer` object under the default `Computers` container — the expected location for a client that joins the domain directly rather than being pre-staged into an OU.

---

## Retiring the Project 03 Lab Deviation

On `SRV-DC01`, opened Group Policy Management → Domain Controllers → Default Domain Controllers Policy → Edit, then navigated to:

```
Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > User Rights Assignment > Allow log on locally
```

Removed the `IT` group from this right, leaving only the default groups.

```powershell
gpupdate /force
```

Re-tested a local logon attempt as `jdoe` directly on `SRV-DC01` — correctly blocked again with the same "sign-in method you're trying to use isn't allowed" error seen originally in Project 03, confirming the domain controller is back to its production-realistic default.

---

# Validation

Verified:

- VM hardware/firmware configuration (EFI, TPM 2.0, Secure Boot) prior to installation
- Windows 11 Enterprise Evaluation installed (`systeminfo`)
- Static DNS configured (`192.168.45.129`)
- Connectivity to `SRV-DC01` (`ping`, after confirming it was powered on)
- Successful domain join (`jamaursec.lab`)
- Computer rename to `WKS-W11-01`
- Domain login as `JAMAURSEC\jdoe`
- Group Policy applied from `SRV-DC01.jamaursec.lab` (`gpresult`)
- `Restrict Control Panel` GPO enforced (both `gpresult` output and an on-screen block)
- `WKS-W11-01` computer object present in Active Directory
- Project 03 DC local-logon deviation successfully removed and re-verified as blocked

---

# Commands

## Connectivity

```powershell
ping SRV-DC01.jamaursec.lab
ping 192.168.45.129
```

## System Verification

```powershell
whoami
systeminfo
```

## Group Policy Verification

```powershell
gpresult /R /SCOPE USER
gpupdate /force
```

---

# Troubleshooting

## VM Name Collision on Creation

Issue:

The "New Virtual Machine" wizard would not accept `WKS-W11-01` as a name — the Name field showed a persistent red/orange validation outline and Finish stayed greyed out, even after filling in hardware and disk settings.

Investigation:

```bash
ls ~/VirtualBox\ VMs/
ls -la ~/VirtualBox\ VMs/WKS-W11-01/
```

Found an existing, empty `WKS-W11-01` folder — left over from an earlier, cancelled attempt at creating the VM.

Resolution:

```bash
rm -rf ~/VirtualBox\ VMs/WKS-W11-01/
```

Recreated the VM afterward; the name was accepted normally.

---

## "No Internet" During OOBE

Issue:

Despite `WKS-W11-01` being attached to the `jamaursec-nat` NAT Network, the OOBE network-connection screen reported "No Internet" and offered to install a network driver.

Resolution:

Selected **"I don't have internet"** instead of troubleshooting the adapter, which proceeded directly into local account setup — the desired outcome anyway, since a local administrator account was needed to perform the domain join. Not independently root-caused; documented as observed behavior rather than a confirmed fix.

---

## Initial Ping Failures to the Domain Controller

Issue:

```
PS C:\Users\localadmin> ping SRV-DC01.jamaursec.lab
Ping request could not find host SRV-DC01.jamaursec.lab. Please check the name and try again.
PS C:\Users\localadmin> ping 192.168.45.129

Pinging 192.168.45.129 with 32 bytes of data:
Request timed out.
Request timed out.
```

Investigation:

Checked VirtualBox Manager and found `SRV-DC01` (Windows Server 2022) was Powered Off.

Resolution:

Started `SRV-DC01` and allowed it to fully boot. Re-ran the ping:

```
Pinging 192.168.45.129 with 32 bytes of data:
Reply from 192.168.45.129: bytes=32 time<1ms TTL=128
Reply from 192.168.45.129: bytes=32 time<1ms TTL=128
Reply from 192.168.45.129: bytes=32 time<1ms TTL=128
Reply from 192.168.45.129: bytes=32 time<1ms TTL=128

Ping statistics for 192.168.45.129:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)
```

---

## Missed the Domain Join Success Dialog

Issue:

Clicked past the "Welcome to the jamaursec.lab domain" confirmation dialog before capturing a screenshot.

Resolution:

Re-triggered the same confirmation before restarting and captured it on the next pass. No domain leave/rejoin cycle was ultimately needed.

---

## Windows Computer Name vs. VirtualBox VM Name

Issue:

After the domain join, System Properties still showed the computer name as the auto-generated `DESKTOP-UM40F7A`, despite the VM being named `WKS-W11-01` in VirtualBox since creation.

Resolution:

Renamed the computer via System Properties → Change → Computer name → `WKS-W11-01`, which required an additional restart to apply. The VirtualBox VM name and the guest OS hostname are independent settings.

---

# Lessons Learned

- The VirtualBox VM name and the guest OS's computer name are unrelated settings — renaming one has no effect on the other.
- Leftover VM folders from a cancelled "New Virtual Machine" wizard attempt block reuse of that VM name until manually deleted.
- A "No Internet" status during Windows Setup doesn't necessarily indicate a broken NAT Network — for a machine headed toward a domain join anyway, proceeding offline into local account setup is a reasonable path, not just a workaround.
- Before troubleshooting client-side DNS or firewall configuration, confirm the target server is actually running and fully booted — an unstarted VM produces the same symptoms as a real network problem.
- Validating Group Policy from a genuine domain-joined client is a stronger, more representative test than a temporary local-logon exception on the domain controller, and retiring that exception once a real client exists restores the DC to a realistic security posture.

---

# Skills Demonstrated

## Virtualization

- Windows 11 VM deployment with EFI, TPM 2.0, and Secure Boot
- VirtualBox troubleshooting (leftover VM folder / name collision)

## Windows Client Administration

- OOBE / offline account setup
- Static DNS configuration
- Domain join
- Computer rename

## Active Directory

- Domain authentication verification
- Active Directory Users and Computers (computer object review)

## Group Policy

- `gpresult` verification from a real domain-joined client
- Removing a temporary User Rights Assignment exception
- `gpupdate /force`

## Professional Skills

- Enterprise Documentation
- Troubleshooting
- Verification
- Change Management (retiring a lab-only deviation)

---

# Project Outcome

Successfully deployed a Windows 11 Enterprise Evaluation client, joined it to `jamaursec.lab`, renamed it to `WKS-W11-01`, and confirmed the `Restrict Control Panel` Group Policy Object applies correctly from a genuine domain-joined client — both through `gpresult` output and a real on-screen restriction. Confirmed the client's computer object in Active Directory, then retired the Project 03 lab-only DC local-logon deviation and re-verified the domain controller's default local-logon restriction is back in effect.

This completes the identity-and-client validation loop started in Project 03 and provides a real client machine for future Home Lab projects to build on.
