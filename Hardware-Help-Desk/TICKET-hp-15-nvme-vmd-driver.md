# IT Service Ticket

**Ticket #:** HWD-2026-003
**Date Opened:** September 20, 2026
**Date of Service:** September 20, 2026
**Status:** 🟢 Closed — Resolved

---

## Device Information

| Field | Detail |
|---|---|
| Device Type | Laptop |
| Make / Model | HP Laptop 15-dy2xxx (SKU 446R4UA#ABA) |
| Device Owner | Self (Ja'Maurian Williams) |
| Reported By | Self |
| Technician(s) | Ja'Maurian Williams |

---

## Reported Issue

Replacing the laptop's original 238GB NVMe drive (INTEL HBRPEKNX0101AH) with a 1TB TeamGroup MP33 NVMe SSD. After physically swapping the drive and booting into Windows 11 Setup from USB install media, Setup reported it could not find the new drive ("We couldn't find any drives. To get a storage driver, click Load driver") — the drive was completely invisible to the installer.

---

## Diagnostic Steps

1. **Confirmed hardware compatibility before the swap** — Used `msinfo32` to identify the exact model/SKU, and confirmed via HP documentation this model has only one M.2 NVMe slot (replacement required, not an add-in).
   - **Conclusion:** New 1TB drive was a supported physical replacement.

2. **Physical swap and first boot attempt** — Installed the TeamGroup MP33 in the single M.2 slot and booted from Windows install USB.
   - **Finding:** Setup's partition screen showed zero drives; "can't find driver" error.

3. **BIOS investigation (AMI BIOS F.33)** — Checked Main, Security, Configuration, and Boot Options tabs for a SATA/RAID mode toggle.
   - **Finding:** No direct AHCI/RAID/VMD mode switch present anywhere in the standard BIOS tabs on this model.

4. **UEFI HII Configuration submenu** — Found under Configuration → UEFI HII Configuration, a page titled "Intel(R) RST 18.1.1.5201 RST VMD Driver" listing the new drive under "Non-RAID Physical Disks."
   - **Conclusion:** Intel VMD (Volume Management Device) mode is active at the chipset level on this model, with no BIOS-exposed way to disable it — the fix had to be a driver, not a BIOS setting.

5. **First driver-extraction attempt (Intel SetupRST.exe, in WinPE)** — Ran `SetupRST.exe -extractdrivers` from within Windows Setup's Shift+F10 command prompt.
   - **Finding:** Command completed with no error but produced no output files — WinPE's minimal environment couldn't execute the installer's actual extraction logic.

6. **Second attempt (Intel SetupRST.exe, via Wine on Ubuntu dev machine)** — Copied `SetupRST.exe` to a Linux machine and attempted extraction there.
   - **Finding:** Plain archive extraction (`7z`) only pulled raw PE binary sections, not the real driver payload. Running the exe under Wine failed with a missing Wine Mono (.NET runtime) dependency; after installing Wine Mono manually, the exe then failed with a `TypeLoadException` — it depends on a separate `Interfaces` assembly that wasn't present, meaning `SetupRST.exe` isn't a self-contained executable.

7. **Pivoted to HP's own driver package** — Downloaded HP's SoftPaq "Intel Rapid Storage Technology Driver" (`sp146929.exe`) from HP's support site for this exact model/SKU instead of Intel's generic installer.
   - **Finding:** `7z` extracted this package cleanly (HP's SoftPaq format didn't require code execution to unpack), producing a complete `F6` driver folder containing `iaStorVD.inf`, `iaStorVD.sys`, and `iaStorVD.cat`.

---

## Root Cause

Intel VMD (Volume Management Device) mode enabled at the chipset/firmware level, with no BIOS-exposed toggle to disable it on this HP model — this hides any NVMe drive from Windows Setup's built-in driver set until the matching Intel RST VMD driver is loaded manually.

---

## Resolution / Action Taken

- Copied the extracted `F6` driver folder to the same USB stick as the Windows install media.
- In Windows Setup, used **Load driver** → browsed to `F6\iaStorVD.inf` → selected **"Intel RST VMD Controller 9A0B"**.
- Drive became visible immediately after loading the driver.
- Discovered the "new" drive was not factory-blank — it carried a full pre-existing partition layout (System, MSR, ~370GB of used space on the Primary partition, Recovery) from prior use.
- Deleted all existing partitions on the drive down to a single unallocated space, then let Setup auto-create fresh System/MSR/Primary/Recovery partitions.
- Completed a clean Windows 11 installation, set up as a new PC (declined restoring from an old Windows Backup to keep the install clean), and named the device `JaMsWin1`.
- Completed the full post-install hardening checklist: standard user account, Windows Security (real-time/cloud-delivered protection, Controlled folder access), Windows Update, Secure Boot verification, Device Encryption, and Startup/installed apps review.
- Confirmed full ~1TB capacity recognized correctly in Disk Management.

## Next Steps

- [x] Complete Windows 11 installation
- [x] Complete full post-install hardening checklist (standard user account, Windows Security settings, Windows Update, Secure Boot verification, Device Encryption, startup/installed apps review)
- [x] Confirm full ~1TB capacity is recognized correctly in Disk Management
- [x] Update ticket status to Closed once verified

---

## Notes / Lessons Learned

- Intel VMD mode can hide an NVMe drive from Windows Setup with zero BIOS-level toggle exposed on some OEM models — always check BIOS submenus (e.g., UEFI HII Configuration) for an RST/VMD controller page before assuming a hardware fault.
- Vendor installer executables like Intel's `SetupRST.exe` are frequently not self-contained — they depend on sibling DLLs/assemblies and full .NET/Mono runtime execution to unpack, so extraction attempts in a minimal environment (WinPE) or via raw archive tools alone will silently fail or produce incomplete output.
- OEM (HP) SoftPaq driver packages can be a simpler, more directly extractable format than the original vendor (Intel) installer for the same underlying driver — worth trying first when a dedicated F6/driver-only download isn't offered directly.
- Never assume a "new" secondhand drive is factory-blank — verify its actual partition state in Setup before installing, since it may carry a full existing partition layout from prior use that needs to be explicitly wiped.
