# IT Service Ticket

**Ticket #:** HWD-2026-002
**Date Opened:** August 24, 2026
**Date of Service:** August 24, 2026 – September 18, 2026
**Status:** 🟢 Closed — Workaround Applied (Root Cause: Unresolved Upstream Kernel Bug)

---

## Device Information

| Field | Detail |
|---|---|
| Device Type | Laptop (2-in-1 convertible) |
| Make / Model | Lenovo 300e 2nd Gen (MT: 82GK), AMD 3015e with Radeon Graphics |
| Device Owner | Ja'Maurian Williams (self) |
| Reported By | Self — personal hands-on project |
| Technician(s) | Ja'Maurian Williams, Drew Burton (Classmate), with USB/ISO assistance from Mr. D (Instructor) |

---

## Background / Setup Process

- Laptop was originally issued by my high school and ran Windows 11 Education Edition.
- Converting it to Linux Mint was one of my first hands-on OS installation projects, done alongside classmate Drew.
- Obtained an 8GB USB flash drive from Mr. D (instructor).
- Downloaded the Linux Mint Cinnamon ISO from Mr. D's office computer, which keeps a shared folder of OS ISOs.
- Used Rufus on my own laptop to burn the Cinnamon ISO onto the USB drive.
- Booted into BIOS, adjusted boot order, and installed Linux Mint Cinnamon onto the laptop.
- Immediately after completing the install and initial setup, the touchpad was found to be non-functional.

---

## Reported Issue

After a fresh install of Linux Mint 22.3 Cinnamon (kernel 7.0.0-30-generic) on the Lenovo 300e 2nd Gen, the built-in touchpad does not respond to any input. The touchscreen and stylus on the same device (ELAN238E:00 04F3:2894) function normally — only the touchpad is affected.

---

## Diagnostic Steps

1. **Device detection check** — Ran `xinput list`. The touchpad (ELAN238E:00) appeared as a recognized input device (id=13).
   - **Conclusion:** Touchpad is detected by the system; not a missing-device issue.

2. **Kernel log review** — Ran `sudo dmesg | grep -i -E "touchpad|i2c|psmouse"`.
   - **Finding:** Repeated error: `i2c_hid_acpi i2c-ELAN238E:00: i2c_hid_get_input: IRQ triggered but there's no data`
   - **Conclusion:** The touchpad is triggering interrupts but the I2C HID driver never receives usable data from it — points to a driver/hardware-communication issue rather than a missing driver.

3. **Physical inspection** — Opened the bottom panel of the laptop and inspected the touchpad ribbon cable and its connector on the motherboard.
   - **Finding:** Cable was fully seated, latch closed, no visible damage.
   - **Conclusion:** Ruled out a loose/damaged physical connection.

4. **GRUB kernel parameter fix, attempt #1** — Added `i2c_hid_acpi.probe_defer=0` to `GRUB_CMDLINE_LINUX_DEFAULT`, ran `update-grub`, rebooted.
   - **Finding:** dmesg showed `i2c_hid_acpi: unknown parameter 'probe_defer' ignored` — parameter was invalid for this kernel and had no effect.

5. **GRUB kernel parameter fix, attempt #2** — Changed parameter to `acpi_enforce_resources=lax i2c_hid_acpi.ignore_wakeup=1`, ran `update-grub`, rebooted.
   - **Finding:** Same `IRQ triggered but there's no data` error persisted. No change in behavior.

6. **System information confirmation** — Used the System Info tool to confirm exact hardware: Lenovo 300e 2nd Gen (82GK), AMD 3015e, kernel 7.0.0-30-generic, Mint 22.3 Cinnamon.

7. **Kernel update attempt** — Ran `sudo apt install linux-generic-hwe-24.04`.
   - **Finding:** Package was already at the newest available version (7.0.0-30.30~24.04.1) for this release channel. No newer kernel available through standard update.

8. **Public bug research** — Searched for the exact hardware/error combination.
   - **Finding:** Located an open, unresolved Ubuntu/Launchpad bug report (**Bug #1976556** — "[Lenovo 300e 2nd GEN] ELAN Touchpad not working") describing the identical symptom on the same laptop model: touchscreen functional, touchpad dead, same dmesg signature. Confirmed by multiple independent users across Ubuntu and Linux Mint installs, with no resolved fix as of the most recent tracked kernel-developer comment (2024).

9. **BIOS/firmware update consideration** — Researched Lenovo's published BIOS update for the 300e 2nd Gen (MT:81M9/82GK).
   - **Finding:** Update is distributed only as a Windows executable; no confirmed reports in the bug thread or elsewhere that a firmware update resolves this specific issue.
   - **Decision:** Deprioritized as a low-probability fix requiring disproportionate effort (would require booting Windows).

10. **Manual driver reload** — Unloaded and reloaded the HID driver stack:
    ```
    sudo modprobe -r hid_multitouch i2c_hid_acpi i2c_hid
    sudo modprobe i2c_hid
    sudo modprobe i2c_hid_acpi
    sudo modprobe hid_multitouch
    ```
    - **Finding:** Device re-enumerated through `hid-multitouch` exactly as at boot, but the same `IRQ triggered but there's no data` error reappeared immediately. No change in functionality.
    - **Conclusion:** Rules out a driver load-order/race condition; confirms the failure occurs at the hardware communication layer between the kernel driver and the ELAN touchpad controller itself.

---

## Root Cause

Confirmed open, unresolved upstream Linux kernel bug affecting the ELAN238E:00 I2C HID touchpad on the Lenovo 300e 2nd Gen (AMD Picasso platform). The `i2c_hid_acpi` driver successfully detects the device and receives interrupt signals from it, but never receives valid data, regardless of kernel parameters, kernel version (up to the latest available at time of testing), or manual driver reinitialization. This is tracked publicly as Launchpad Bug #1976556 and affects multiple users on this exact hardware/OS combination. Not caused by installation error, physical damage, or misconfiguration on this unit.

---

## Resolution / Action Taken

- Systematically ruled out detection failure, physical/cable damage, GRUB/kernel parameter issues, outdated kernel, and driver load-order as causes.
- Identified root cause as a confirmed, still-open upstream kernel bug with no available fix at the OS or firmware level.
- Applied external USB mouse (Razer DeathAdder Essential) as the functional workaround; laptop is fully usable with this in place.
- Ticket closed as "workaround applied" rather than "fixed," since no permanent resolution currently exists upstream.

## Next Steps

- [ ] Periodically check Launchpad Bug #1976556 for an upstream fix or patch
- [ ] Re-test touchpad after future Mint/Ubuntu kernel updates
- [ ] Continue using external USB mouse as the standing workaround
- [ ] Revisit and update this ticket if a fix becomes available

---

## Notes / Lessons Learned

- A device appearing in `xinput list` or `dmesg` only confirms detection — it does not confirm the device is actually passing usable data.
- The dmesg line `IRQ triggered but there's no data` is a specific, searchable diagnostic signature for I2C HID communication failures, not generic noise.
- Cross-referencing an exact hardware model and kernel error message against public bug trackers (Launchpad, GitHub, kernel mailing lists) is an efficient way to determine whether an issue is local/fixable or a known unresolved upstream limitation.
- Not every ticket ends in a full fix — correctly identifying root cause and applying a reasonable workaround is a legitimate and professional resolution, and should be documented as such rather than framed as a failure.
- I2C HID touchpads (common on newer AMD ultrabooks/convertibles) appear more prone to Linux driver quirks than legacy PS/2-style touchpads, which is useful context for future hardware tickets on similar devices.