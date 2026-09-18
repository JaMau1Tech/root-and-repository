# Autopilot & BitLocker Investigation

This document records the investigation into why a standard Windows reinstall could not fully reprovision the device, and the decision to move to Linux instead.

---

# Issue 1 - BitLocker Encryption With No Recovery Key

## Problem

The drive was BitLocker-encrypted, and no recovery key was available.

## Investigation

A full-disk wipe (deleting all partitions during a clean install, or repartitioning entirely for a different OS) destroys the BitLocker volume master key along with the data on disk.

## Resolution

No decryption or key recovery was necessary. The encrypted partitions were overwritten entirely as part of the reinstall/reprovisioning process.

## Result

BitLocker was not an obstacle once a full-disk wipe was the chosen path.

---

# Issue 2 - Windows Setup Forces Autodesk Enrollment

## Problem

After a clean Windows 11 install, the out-of-box setup screen (OOBE) presented a work/school sign-in step instead of offering a local account option.

## Symptoms

```text
Let's set things up for your work or school
Sign in
username@autodesk.onmicrosoft.com
```

## Investigation

This placeholder domain indicated the device's hardware hash was still registered to the previous employer's Windows Autopilot / Intune tenant. Autopilot enrollment is tied to the hardware hash reported to Microsoft, not to anything stored on the local disk, so it survives a clean OS reinstall.

## Steps Attempted

- Ran `oobe\bypassnro` via Shift+F10 to attempt to skip the mandatory network-connection requirement and reach a local account setup path
- Rebooted and returned to the network/OOBE flow

## Resolution

`bypassnro` did not remove the enrollment prompt. It reappeared after reboot, consistent with an actively enforced Autopilot profile rather than cached local branding.

## Result

Client-side OOBE bypass was not effective against this enrollment.

---

# Issue 3 - No Response From Original Employer's IT

## Problem

Autopilot/Intune de-enrollment must be performed on the tenant side; there is no supported end-user method to remove a device from another organization's Autopilot registration.

## Steps Attempted

- Direct outreach to the former employer's IT department requesting the device be released from enrollment

## Result

No response was received. Continuing to escalate toward Windows-side circumvention (hardware hash spoofing, MDM registry tampering, third-party de-enrollment tools) was ruled out, since the enrollment was still legitimately active and the decision to release the device wasn't ours to make unilaterally.

---

# Decision - Move to Linux Mint

Rather than continue pursuing a Windows-based workaround, the device was reprovisioned with Linux Mint (Cinnamon) instead. Windows Autopilot/Intune enrollment has no equivalent hook into a non-Windows OS, so this sidesteps the block entirely without contesting the underlying control.

## Steps Taken

- Checked BIOS (F1) for a supervisor password lock — none found
- Disabled Secure Boot in BIOS/UEFI for installer compatibility with this generation's firmware
- Set USB boot via the one-time boot menu (F12)
- Booted the Linux Mint Cinnamon installer and selected "Erase disk and install Linux Mint," overwriting the BitLocker-encrypted partitions entirely
- Applied post-install system updates
- Installed end-user applications (Discord, Telegram, Google Chrome)

## Result

Fully functional, locally-administered Linux system with no residual tie to the former employer's device management tenant.

---

# Skills Practiced

- BitLocker behavior under full-disk reprovisioning
- Windows Autopilot / Intune enrollment mechanics
- Recognizing the limits of client-side workarounds against an actively enforced enterprise control
- BIOS/UEFI configuration (Secure Boot, boot order, supervisor password checks)
- Judgment in choosing a legitimate resolution path over continued circumvention
