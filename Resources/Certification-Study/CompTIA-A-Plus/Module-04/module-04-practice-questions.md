# Module 4 Practice Questions

*Troubleshooting PC Hardware — CompTIA A+ Core 1 (220-1201)*

This module has real logged quiz/lesson-review results (4.1.11, 4.2.14, 4.3.10, 4.7, 4.8), all folded into the "Quiz & Review Key Takeaways" section of the study notes. The questions below are built from that confirmed content, expanded into full option-by-option reasoning.

---

## 4.1 — BIOS and UEFI

**Q1.** A fresh, unsigned Linux installer fails to boot on a system with Secure Boot enabled. What is the correct fix?

A. Reset the TPM
B. Disable Secure Boot to allow the unsigned bootloader
C. Replace the motherboard
D. Enable legacy BIOS mode permanently

**Correct: B.**
Why: Stated directly in the Key Takeaways — an unsigned OS (like a fresh Linux install) is blocked by Secure Boot specifically, and the direct fix is disabling Secure Boot to allow it to boot.

- **A is wrong** — this confuses Secure Boot with TPM. Secure Boot blocks untrusted bootloaders at boot time; TPM generates/stores keys and verifies hashes — they're related but distinct functions, a mix-up the notes explicitly warn against.
- **C is wrong** — this is a firmware setting issue, not a hardware fault.
- **D is wrong** — switching to legacy BIOS mode is a much bigger, unnecessary change when disabling one feature (Secure Boot) solves it directly.

---

**Q2.** TPM has no support on a given system, and a drive needs to be moved to a new machine with encrypted keys intact. What's the correct tool?

A. Reinstall the OS
B. HSM (Hardware Security Module) — a portable alternative to TPM
C. Reset the BIOS to defaults
D. Enable Secure Boot

**Correct: B.**
Why: Stated directly in the Key Takeaways — HSM is TPM's portable alternative when TPM isn't supported (or is damaged, or a disk needs to move to a new machine) — explicitly NOT a performance or backup tool, a distinction the notes call out directly.

- **A is wrong** — reinstalling the OS doesn't solve moving encrypted keys to new hardware.
- **C is wrong** — resetting BIOS defaults doesn't address the underlying lack of TPM support.
- **D is wrong** — Secure Boot is a separate boot-verification feature, unrelated to key storage/portability.

---

**Q3.** What is the difference between "Quiet" fan mode and "Fanless" mode?

A. They are the same setting under different names
B. Quiet = reduced speed with higher tolerated temps; Fanless = no active cooling at all
C. Quiet = no active cooling; Fanless = reduced speed only
D. Fanless mode is only available on laptops

**Correct: B.**
Why: Stated directly in the Key Takeaways as an explicit distinction — these two are easy to conflate but are functionally different settings.

- **A is wrong** — this is the exact confusion the notes flag as a takeaway to avoid.
- **C is wrong** — reverses the two definitions.
- **D is wrong** — nothing in the notes restricts Fanless mode to laptops; it's listed as one of the general firmware fan modes (Balanced/Cool/Quiet/Fanless/Custom).

---

## 4.2 — Power and Disk Issues

**Q4.** A system's RAID configuration utility cannot be accessed at all, even though the array was working yesterday. What does this most likely indicate?

A. "Array missing" — too many disks have failed relative to RAID tolerance
B. Controller failure
C. A single disk has failed and the array is simply degraded
D. The RAID array needs to be rebuilt

**Correct: B.**
Why: Stated directly in the Key Takeaways — being unable to access the RAID config utility at all points specifically to controller failure, distinct from "array missing" (which means too many disks failed relative to tolerance).

- **A is wrong** — "array missing" is a different symptom (too many failed disks) with the utility itself still presumably reachable; being unable to reach the utility AT ALL is the controller-failure signature.
- **C is wrong** — a single degraded disk still leaves the array accessible and marked "degraded," not totally inaccessible.
- **D is wrong** — a rebuild requires access to the RAID utility in the first place, which is the very thing that's failing here.

---

**Q5.** A drive makes a grinding/clicking noise. What is the correct response?

A. Run chkdsk and a malware scan
B. Defragment the drive
C. Back up data immediately and replace the drive — this is HDD mechanical failure
D. Ignore it unless performance also drops

**Correct: C.**
Why: Stated directly in the Key Takeaways — grinding/clicking/scraping noise is a clear mechanical HDD failure signature (doesn't apply to SSDs, which have no moving parts), and the correct response is backup + replacement, not defrag or malware scan.

- **A is wrong** — this is explicitly named as the WRONG response to this specific symptom; chkdsk/malware scans address logical issues, not mechanical failure.
- **B is wrong** — defragmentation addresses fragmentation-related slowness, not mechanical failure, and can actually stress a failing drive further.
- **D is wrong** — mechanical noise is itself the actionable symptom; waiting for a performance drop risks total data loss first.

---

## 4.3 — System and Display Issues

**Q6.** A computer that was recently upgraded with new RAM is now noticeably slower. What should be checked FIRST?

A. Run a full system diagnostic across every subsystem
B. Check whether the upgrade accidentally broke dual-channel mode
C. Replace the power supply
D. Reinstall the operating system

**Correct: B.**
Why: Stated directly in the Key Takeaways — post-upgrade sluggishness should be checked against the specific thing that changed (e.g., dual-channel mode, SSD config) before broader diagnostics, directly echoing Module 1's "what changed?" principle.

- **A is wrong** — this skips the most efficient first step (checking what changed) in favor of a broad, slower diagnostic sweep.
- **C is wrong** — nothing about a RAM upgrade implicates the power supply specifically.
- **D is wrong** — a full OS reinstall is a drastic, unnecessary step before checking the obvious recent change.

---

**Q7.** A monitor shows "no signal." Separately, another monitor shows a dim, ghosted image with power clearly on. How should these two be diagnosed differently?

A. Both are backlight failures
B. "No signal" = cable/connection issue; blank/dim with power on = bulb/backlight issue
C. Both are cable issues
D. Both require replacing the monitor

**Correct: B.**
Why: Stated directly in the Key Takeaways as a direct contrast — these are different symptom categories requiring different diagnostic starting points.

- **A is wrong** — "no signal" specifically points to cable/connection, not backlight.
- **C is wrong** — the dim/ghosted-with-power symptom points to bulb/backlight, not cabling.
- **D is wrong** — neither symptom is stated to require outright replacement as the first step; both should be diagnosed (cable swap, or bulb/backlight check) before assuming replacement is needed.

---

**Q8.** After a CPU upgrade, a system shuts down consistently after about 15 minutes of use. What should be checked FIRST?

A. RAM compatibility
B. Fan power connection and thermal paste application
C. PSU wattage rating
D. Motherboard BIOS version

**Correct: B.**
Why: Stated directly in the Key Takeaways — post-CPU-upgrade shutdown after ~15 minutes should always prompt checking fan power + thermal paste application first — a classic overheating-from-installation-error pattern.

- **A is wrong** — RAM compatibility issues typically cause boot failures or instability, not a consistent 15-minute-delayed shutdown pattern, which is a thermal signature.
- **C is wrong** — PSU wattage issues tend to cause immediate instability/no-boot, not a delayed, consistent time-based shutdown.
- **D is wrong** — BIOS version issues aren't the notes' identified pattern for this specific delayed-shutdown symptom.

---

**Q9.** A CPU fails prematurely after a repair visit. What is the most likely cause, per the notes?

A. Heat damage
B. Magnetism from a nearby tool
C. ESD (electrostatic discharge)
D. Normal end-of-life wear

**Correct: C.**
Why: Stated directly in the Key Takeaways — CPU premature failure is commonly caused by ESD, explicitly NOT heat (thermal protection exists to prevent heat damage) or magnetism.

- **A is wrong** — explicitly ruled out; thermal protection mechanisms exist specifically to prevent heat from causing this kind of failure.
- **B is wrong** — explicitly ruled out as a cause in the notes.
- **D is wrong** — the notes attribute this to a specific handling-related cause (ESD) during a repair visit, not generic wear.

---

## Missed-Concept Watchlist

The source notes' Quiz & Review Key Takeaways section (covering lesson reviews 4.1.11, 4.2.14, 4.3.10, and the Module 4.7 Quiz/4.8 Checkpoint) does not explicitly flag which individual questions were missed vs. answered correctly on the first attempt — only the consolidated list of takeaways above. Nothing is logged here as a confirmed miss; if you recall specific questions you got wrong, they can be added here with the reasoning that would have gotten them right.
