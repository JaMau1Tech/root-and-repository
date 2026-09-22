# HWD-2026-004: HP t620 Thin Client — No Power / Storage Upgrade

**Date Opened:** Sept 21, 2026
**Status:** 🟢 Closed — Resolved
**Device:** HP t620 Thin Client (G4U29UA#ABA)

## Summary
Mini PC (HP t620 Thin Client) provided by client, unresponsive to power — no LED,
no fan, no POST. Diagnosed and resolved; unit repurposed from HP ThinPro to
Xubuntu 26.04 LTS running from an internally-mounted NVMe-via-USB adapter.
Onboard Wi-Fi found to be unsupported by the current kernel driver; resolved
via USB Wi-Fi adapter.

## Device Info
- **Model:** HP t620 Thin Client (dual-core)
- **P/N:** G4U29UA#ABA | **Spare:** 773948-001
- **Regulatory Model:** TPC-I004-TC
- **CPU:** AMD GX-217GA w/ Radeon HD
- **RAM:** 4GB
- **Original Storage:** SanDisk SSD U110, M.2 2242, 8GB SATA (HP P/N 742783-001)
- **PSU spec:** 19.5V, 3.33A (65W)
- **Onboard Wi-Fi:** Broadcom BCM4352 802.11ac (HP OEM variant), PCI ID [14e4:43b1]

## Reported Issue
Unit would not power on. No indicator lights, no fan spin, no response to
power button.

## Diagnostic Steps
1. Visual inspection after opening chassis — no visible board damage, swollen
   caps, or corrosion. *(see photos 01–02)*
2. Tested original power adapter — wall-side indicator light was active,
   giving false impression adapter was functional.
3. Swapped in a known-good 19.5V/3.33A HP charger — unit powered on
   immediately, booted to HP ThinPro desktop. *(see photos 03–06)*
4. Confirmed root cause: original charger's DC output had failed despite
   AC-side indicator light remaining lit. *(original charger label, photo 05)*

## Root Cause
Failed AC adapter (DC output dead). Board, RAM, and original storage were
all functional — confirmed by successful ThinPro boot.

## Resolution / Additional Work

### Power
Replaced non-functional charger with known-good HP 65W unit (19.5V/3.33A,
same connector spec).

### Storage
- Client requested OS change to Xubuntu 26.04 LTS. Original internal drive
  (SanDisk U110, M.2 2242, 8GB SATA — photo 09) was undersized for the
  install (partition screen confirming ~8GB, photo 08).
- Removed original SanDisk 8GB drive (retained as spare/fallback to ThinPro).
- Identified a Samsung PM991a 256GB NVMe drive (M.2 2280) as a candidate
  upgrade; confirmed the t620's AMD GX-217GA platform is SATA-only and does
  not support NVMe natively (drive comparison, photo 10).
- Installed Xubuntu 26.04 LTS to the 256GB NVMe via a USB 3.0 NVMe-to-USB
  adapter (photo 11), since the drive cannot be used in the internal M.2
  slot directly. Drive appeared as a ~256GB target in the installer
  (BitLocker notice from prior Windows use, photo 12), erased and installed
  cleanly.
- Adapter board was mounted **inside** the chassis using an available
  internal USB header, rather than left exposed outside the case — keeps
  the connection secure against being bumped loose.
- Verified boot device priority set correctly; confirmed stable, repeatable
  boot with case fully reassembled and closed (photo 13).

### Wi-Fi (driver-level incompatibility)
- Onboard Broadcom BCM4352 card confirmed present via `lspci` but never
  bound to a working driver.
- `sudo apt install bcmwl-kernel-source` — package no longer exists in
  26.04 repos (deprecated in favor of in-kernel `brcmfmac`).
- Loaded `brcmfmac` manually (`sudo modprobe brcmfmac`) — module loaded
  successfully but `nmcli device status` still showed no `wifi` device.
- `sudo lspci -k -s <addr>` showed **`Kernel driver in use: bcma-pci-bridge`**
  — the generic bus bridge driver, not a working Wi-Fi driver — confirming
  `brcmfmac` never actually bound to the device.
- Cross-referenced exact PCI ID `[14e4:43b1]` (HP OEM variant, subsystem
  "Hewlett-Packard Company Device 2154") against `modinfo brcmfmac`'s
  supported-device table — **no match**.
- **Conclusion:** this specific OEM BCM4352 variant is not a firmware or
  configuration issue; it is genuinely absent from the in-kernel
  `brcmfmac` driver's supported-ID table on this kernel (7.0.0-14-generic).
  The legacy proprietary `wl` driver (`broadcom-sta-dkms`) is effectively
  unmaintained and unlikely to build against a modern kernel, so it was not
  pursued.
- **Resolution:** USB Wi-Fi adapter (Realtek RTL8811AU/RTL8188-based
  recommended for native in-kernel Linux support, no compiling required).

## Parts Used
- USB 3.0 M.2 NVMe adapter (M-key)
- Samsung PM991a NVMe 256GB (client-supplied)
- Replacement HP 65W AC adapter (19.5V/3.33A)
- USB Wi-Fi adapter (Realtek-chipset, Linux-native)

## Activity Log
| Date | Action |
|------------|---------------------------------------------------------------|
| 2026-09-21 | Ticket opened. Diagnosed dead AC adapter via known-good charger swap. Unit powers on, boots to ThinPro. |
| 2026-09-21 | Client requested OS change. Removed 8GB internal drive (undersized), installed Xubuntu 26.04 LTS to 256GB NVMe via internally-mounted USB adapter. |
| 2026-09-21 | Verified stable boot with case reassembled. Boot device priority confirmed. |
| 2026-09-21 | Diagnosed onboard Wi-Fi (Broadcom BCM4352, HP OEM variant) as non-functional under Xubuntu 26.04. Confirmed via kernel module tracing (`brcmfmac` loads but never binds to device; `lspci -k` shows `bcma-pci-bridge` still claiming the slot). Cross-referenced exact PCI ID `[14e4:43b1]` against `modinfo brcmfmac` — no match, confirming this OEM variant is absent from the driver's supported-device table on this kernel. Root cause: hardware/driver incompatibility, not a missing firmware file or misconfiguration. Resolution: USB Wi-Fi adapter. |

## Follow-up / Outstanding
- Onboard Wi-Fi unsupported at driver level — resolved via USB Wi-Fi
  adapter rather than onboard card. No further action needed once dongle
  is in hand and confirmed working.
- Timezone/clock sync pending stable network connectivity.

## Photos
See `/photos` folder for the full set from this ticket:
- `01–02`: chassis opened, initial inspection
- `03–04`: known-good charger power-on test
- `05`: original (failed) charger label/spec
- `06`: HP ThinPro desktop booted (confirms board/RAM/storage functional)
- `07–08`: Xubuntu installer boot and partition screen (8GB internal drive)
- `09`: original SanDisk U110 8GB module label
- `10`: SanDisk 8GB vs. Samsung NVMe 256GB drive comparison
- `11`: NVMe-to-USB adapter board
- `12`: installer disk-selection screen (BitLocker notice, NVMe target)
- `13`: Xubuntu desktop running from NVMe, post-reassembly
- `14–26`: additional in-progress photos from the diagnostic session

## Notes
Good example of adapter-vs-board misdiagnosis risk: AC-side indicator
lights do not confirm DC output is functional. Always verify output voltage
directly when a "known-powered" adapter still yields no response.

Also a useful diagnostic case for driver-vs-hardware troubleshooting: confirmed
via `lspci -k` (driver bound), `modinfo` (device ID lookup), and `dmesg`
(firmware/probe tracing) that this specific OEM Wi-Fi card variant is not a
firmware issue but a genuine gap in kernel driver support — worth documenting
as a repeatable diagnostic pattern for future "card loads but never connects"
cases.
