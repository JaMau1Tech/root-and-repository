# ThinkPad Deprovisioning & Recovery

This project documents reprovisioning a corporate-issued laptop after its original employer released it to a former employee without a formal device offboarding.

The device was BitLocker-encrypted with no recovery key, and a standard Windows reinstall was blocked by residual enterprise device management (Windows Autopilot / Intune enrollment). The project covers the investigation into that block, the decision to move to a different operating system instead of pursuing a Windows-side workaround, and the post-install hardening and hardware diagnostics that followed.

---

# Project Status

**Status:** ✅ Completed

Device is fully reprovisioned, hardened, and in active use by the end user (family member).

---

# Objective

Restore a decommissioned corporate laptop to a fully functional, locally-administered system, without:

- The original corporate owner's credentials
- A BitLocker recovery key
- Continuing to pursue circumvention of an enterprise device-management control that was still legitimately active

---

# Project Structure

```text
ThinkPad-Deprovisioning/
├── README.md
├── docs/
│   ├── autopilot-bitlocker-investigation.md
│   └── shutdown-diagnosis.md
└── screenshots/
    └── README.md
```

---

# Tools Used

- Windows 11 installation media
- Linux Mint Cinnamon (installer)
- BIOS/UEFI setup (Secure Boot, boot order)
- `upower` (battery diagnostics)
- `lm-sensors` (thermal diagnostics)
- `journalctl` (system log review)
- `ufw` / `gufw` (firewall)
- `lspci` (driver verification)

---

# Outcome

Standard Windows reinstallation could not clear the device's Windows Autopilot/Intune enrollment, since that enrollment is tied to the device's hardware hash on Microsoft's side rather than anything stored on the local disk. After confirming the enrollment was still actively enforced and outreach to the original employer's IT went unanswered, the device was reprovisioned with Linux Mint instead — a legitimate way to resolve the practical problem without contesting an enterprise control that wasn't yet released.

The device is now fully functional, hardened with a UFW firewall baseline, and confirmed running the correct wireless driver. A reported ~2-minute post-boot shutdown was investigated and ruled out as a battery or thermal fault through direct diagnostics; it has not recurred under normal use.

---

# Skills Practiced

- BitLocker behavior under full-disk reprovisioning
- Windows Autopilot / Intune enrollment mechanics
- Recognizing the limits of client-side workarounds against an actively enforced enterprise control, and choosing a legitimate resolution path instead
- BIOS/UEFI configuration
- Linux installation and post-install hardening
- Hardware diagnostics (battery health, thermal monitoring, driver verification)
- Systematic troubleshooting (hypothesis → test → verify → document)

---

# Lessons Learned

- A full-disk wipe removes BitLocker's encryption key along with the data, so a missing recovery key does not block reprovisioning through a clean install.
- Windows Autopilot/Intune enrollment persists across OS reinstalls because it is tied to the hardware hash reported to Microsoft, not to local disk state.
- `bypassnro` is not a reliable way to defeat a genuinely enforced Autopilot profile.
- When a legitimate enterprise control is still active and the owning organization is unresponsive, switching to an unaffected operating system can resolve the practical problem without contesting the control itself.
- Ruling out causes with direct evidence (a battery report, sensor data, a driver check) is a useful result on its own, even without a single definitive root cause for an intermittent symptom.
