# Module 4 Study Notes

*Troubleshooting PC Hardware — CompTIA A+ Core 1 (220-1201)*

## 4.1 — BIOS and UEFI

### 4.1.1 — BIOS and UEFI

Firmware = code in flash memory that initializes hardware before the OS
loads. BIOS = legacy, text/keyboard-only. UEFI = modern, GUI + mouse
support.

- UEFI advantages: 64-bit support, GUI/mouse, network boot, better
    boot security, can still fall back to legacy BIOS mode

- Setup access key varies by vendor: Esc/Del/F1/F2/F10/F12 — press
    during the vendor logo screen

- Missed the key prompt? Shift-click Restart from the Windows logon
    screen → reaches UEFI boot options

- Legacy BIOS nav: arrow keys, Esc = back, exit choices = save vs
    discard changes, can reload defaults

- UEFI = mouse-supported GUI, but advanced menus may still need
    keyboard

### 4.1.3 — Boot and Device Options

Boot order = the sequence firmware searches devices for a bootable
OS/boot manager.

- Fixed disk: SATA → lowest-numbered port for boot drive; NVMe
    (M.2/PCIe) = faster, common modern default

- Optical drive: set top priority only temporarily for install/repair
    from disc

- USB: needs to be formatted as bootable; used for OS installs &
    recovery tools

- Network/PXE: boots via network adapter from a configured server —
    common for enterprise imaging

- Wrong boot device symptom → check boot order first

### 4.1.4 — USB Permissions

Firmware can enable/disable controllers/adapters at the hardware level,
including USB — a security control against unauthorized devices,
malware, and data exfiltration.

- Can control individual ports or all USB ports depending on the setup
    program

- Example security tab options: USB Interface, External Ports,
    Bluetooth, CMOS Camera, Card Reader — each Lock/Unlock

- ⚠ Locking is often all-or-nothing per option (e.g., 'Locked'
    disables ALL USB devices)

- Enterprise use: locking USB at the firmware level is OS-independent
    and can't easily be bypassed

### 4.1.5 — Fan Considerations

Clean fans regularly — dust obstructs airflow and causes overheating.
Balance intake/exhaust airflow; avoid pushing hot air downward.

- Fan modes: Balanced / Cool / Quiet / Fanless / Custom — found
    under Cooling/Power/Advanced in firmware

- Custom mode = manual, personalized fan speed control

- Minimum temp threshold = when fans kick in; Duty cycle % = fan speed
    (higher % = faster)

- Firmware displays live temps from sensors near each fan connector

- Temp monitoring: manually via BIOS/UEFI (F2/Del/F12/Esc) OR
    third-party OS-level apps

### 4.1.6 — Boot Passwords and Secure Boot

- Supervisor/Setup password = protects BIOS/UEFI settings access

- User/System password = locks the whole system pre-boot; must be
    shared with all users → weakens security; best for
    non-interactive-logon machines only

- Secure Boot = UEFI-only feature; verifies bootloader is
    signed/trusted via cryptographic keys before allowing boot

- Modified/unsigned bootloader = blocked → protects against boot-level
    malware

- Pre-loaded keys: Microsoft, Fedora, openSUSE, Ubuntu; keys can be
    added/removed; Secure Boot can be disabled

- Modern systems (e.g., Windows 11) often require UEFI + Secure Boot
    enabled

### 4.1.8 — Trusted Platform Modules

Encryption = reversible with the correct key (confidentiality). Hashing
= one-way, verifies integrity, not reversible.

- TPM = hardware chip storing certs/keys/hashed passwords; has a
    unique unchangeable endorsement key = root of trust

- TPM checks hashes of firmware/bootloader/OS kernel at boot to detect
    tampering

- TPM keys are isolated from OS/apps, tamper-resistant, harder to
    extract than software-stored keys

- BitLocker = real-world example using TPM for key storage

- TPM managed via BIOS/UEFI (enable/disable/reset) and from within the
    OS

- HSM = removable USB device storing crypto keys; portable
    alternative/backup to TPM (no TPM support, TPM damaged, or moving an
    encrypted disk to a new machine)

- HSM requires authentication (password/PIN/fingerprint) to access
    stored keys

## 4.2 — Power and Disk Issues

### 4.2.1 — Troubleshoot Power Issues

PSU boot sequence: AC→DC conversion → 12V first (spins fans/disks) →
tests 5V/3.3V → sends 'power good' signal to CPU.

- No-power diagnosis starts with: LEDs lit? Fans audible?

- Isolation order: check other equipment → test wall socket → verify
    PSU connections → try another cable/fuse → disconnect extra devices
    → test PSU with multimeter/tester

- Disconnecting extra devices fixes it → PSU underpowered OR one
    device is faulty

- ⚠ PSUs are NOT user-serviceable — never open the case

- Suspected bad PSU → don't leave powered on unattended; watch for
    smoke/fire/smell/noise → shut off immediately

- No cause found after full isolation → likely faulty motherboard or
    PSU

### 4.2.3 — Troubleshoot POST Issues

POST = firmware diagnostic run after the power good signal, before OS
load. Modern PCs boot fast/silently — logo screen shown, messages only
on error.

- Power present + fans spinning + blank screen + no beeps → check:
    what changed (firmware update?) → reset → cabling/adapter seating →
    faulty device isolation → PSU (fans ≠ power good signal necessarily
    sent) → CPU/firmware fault

- Jumpers misconfigured after service = possible silent boot blocker

- Beep codes are manufacturer-specific; verify against vendor docs

- Key beep meanings: No beep = PSU/motherboard/speaker fault;
    Continuous = memory issue; 1 long+1 short = motherboard; 1 long+2-3
    short = video adapter; 3 long = stuck key

### 4.2.5 — Troubleshoot Boot Issues

After POST: system checks boot devices in configured order; no bootable
device found → error, boot halts.

- Wrong boot device → check for interfering removable media
    (USB/disc) + verify boot order

- Fixed disk not detected checklist: 1) Power (LED, spin-up,
    connector) 2) Data cable (damage, both ends connected) 3) UEFI/BIOS
    (drive enabled? SATA mode AHCI vs RAID correct?) 4) M.2/NVMe
    (properly seated + detected in firmware)

- Troubleshoot in layered order: physical/power → cabling → firmware
    detection → firmware config

### 4.2.7 — Troubleshoot Boot Sector Issues

Boot sector issues are suspected only after power/cabling are ruled out.
Corruption causes: disk faults, power failure, bad multi-OS install,
malware.

- MBR: first sector only, single point of failure, one active primary
    partition, uses BCD (Windows) or GRUB/LILO (Linux)

- GPT: not single-sector limited, more robust/flexible, more reliable
    partition identification

- Boot sector corruption error messages: 'Boot device not found,'
    'OS not found,' 'Invalid drive specification'

- Blank screen ≠ automatically boot sector — check display
    cable/connection first

- Malware-caused → antivirus boot disk (scan + repair boot sector); no
    recovery disk → use OS setup disk's built-in repair options

### 4.2.8 — Troubleshoot OS Errors and Crash Screens

After boot sector loads, errors shift from hardware-focused to mostly
software/driver-focused.

- BSOD = Windows-only crash screen; indicates memory faults,
    driver/device problems, or file corruption

- BSOD causes: bad/incompatible drivers, corrupted system files,
    defective hardware, overheating/power issues

- Troubleshoot BSOD: scan on-screen QR code → check System log
    'BugCheck' entry, note first hex value and search online → memory
    dump available if under support contract

- macOS equivalent = spinning pinwheel; Linux equivalent = kernel
    panic / 'Something has gone wrong'

### 4.2.9 — Troubleshoot Drive Availability

HDD failure: early (defect) or late (wear) — mechanical. SSD failure:
write-cycle wear on memory cells — no moving parts.

- Grinding/clicking/scraping noise = HDD mechanical failure (doesn't
    apply to SSD)

- No LED activity = power/connection issue (single drive) or
    missing/failed array (RAID)

- Constant LED activity = low RAM (paging), bad software/malware, OR
    failing disk

- Bootable device not found = file corruption, faulty drive, OR RAID
    controller not detecting array member(s)

- Missing in OS = check init/partition/format first; not detected at
    all = hardware/cable fault

- Read/write failure ('cannot read from source disk') = bad sectors
    (HDD)/bad blocks (SSD) → run chkdsk, increasing count = imminent
    failure

- Any of these symptoms → back up immediately + replace drive

### 4.2.11 — Troubleshoot Drive Reliability and Performance

S.M.A.R.T. = built-in disk self-diagnostic, can proactively alert the OS
to failure.

- Run diagnostics via vendor utilities, bundled system diagnostics, or
    Windows/third-party SMART tools

- Tests report damage + performance stats like IOPS

- Metrics below baseline = drive likely faulty; metrics normal = look
    elsewhere (app load, fragmentation [HDD only], low free space)

- Bad sectors (HDD) / bad blocks (SSD) → firmware marks them unusable
    going forward

- ⚠ SSD file recovery is generally not possible without specialized
    tools (unlike HDD)

### 4.2.12 — Troubleshoot RAID Failure

RAID protects against single-disk failure via mirroring or parity;
presented to the OS as one volume.

- Device failure (single disk) → volume shows 'degraded,' data still
    accessible, still bootable if configured

- RAID 0 = NO redundancy — one disk fails, whole volume dies; RAID 0
    = speed-focused, not reliability-focused

- Array failure = most desktop RAID tolerates only 1 lost disk;
    replace ASAP

- Hot swap supported → insert new disk → rebuild via RAID config
    utility (hardware) or OS utility (software); rebuild = heavy
    temporary performance hit

- ⚠ Never hot-swap a healthy disk — check for red LED (failure
    indicator); always back up before swapping

- 'Array missing'/unavailable volume = too many failed disks OR
    controller failure; boot volume affected = OS won't start

- Controller failure = data usually recoverable, possible corruption
    from interrupted writes; fix = new controller or move disks to
    another system

- Can't access RAID config utility at all = likely controller failure
    itself

### 4.2.13 — Real-World Storage/RAID Troubleshooting (Industry Interview)

- Real-world SSD issues often stem from misconfiguration (mixing
    different SSD models/specs), not hardware failure

- Spinning HDDs vulnerable to heat, temperature, vibration; audible
    whine + orange/red LED = failure warning signs

- Common modern spinning-disk errors: 'target not found,' data
    corruption — increasing as disks age

- SSD diagnostic approach: Disk Management/BIOS first (confirm system
    sees the disk) → Performance Monitor → vendor/proprietary software
    (config + firmware)

## 4.3 — System and Display Issues

### 4.3.1 — Troubleshoot Component Issues

Lockups/shutdowns/crashes → often software/corruption/malware, not
hardware — rule that out first.

- Pattern-based errors (e.g., after running a while) → suggests a
    thermal issue

- Check PSU for stable voltage before suspecting other hardware

- Vendor hardware diagnostics often run from firmware, not OS

- No diagnostic tools available → fall back to physical/visual
    inspection

- RAM: needs firm, EVEN pressure on both sides to seat correctly —
    most 'failure to POST' RAM issues are installation issues, not
    dead sticks

- CPU: needs minimal/no force to seat — real pressure needed =
    something's misaligned, stop and recheck; verify seating BEFORE
    attaching the heat sink

- Fan whine = end-of-life, bad power connection, or physical
    interference (cable rubbing) — reseat/reconnect first

### 4.3.2 — Overheating

Hot to the touch = check for overheating; burning smell/smoke = likely
PSU, shut down immediately. Dust-clogged vents can also cause a burning
smell without actual failure.

- Diagnostic techniques: temp sensors (compare to vendor docs), CPU
    fan (connected/clogged/undersized), heat sink (snug fit, fresh
    thermal paste), blanking plates (cover unused case holes),
    environment (room temp/dust, avoid radiators/direct sun)

- A fan sized for an old CPU may be inadequate after a CPU upgrade —
    check cooling capacity, not just fit

- Thermal stress side effects: loosened connectors, shifted
    components, widening hairline PCB cracks — some visually
    detectable

### 4.3.3 — Physical Damage

Physical damage most often hits peripherals/ports/cables; internal
damage is more likely after transit. Even small case cracks/dents can
signal a fall causing hidden internal damage.

- Peripheral not working → check port/cable pins (bent/broken/dirty) +
    full cable length

- Motherboard damage causes: ESD/electrical spikes/overheating (chip
    damage), careless insertion (bent pins), dirt/chip creep (adapter
    loosens over time from thermal cycling)

- Visible damage signs: liquid spills, dust clogging, scorch marks
    (blown component), swollen/bulging capacitors

- Suspected motherboard damage → use diagnostic software to confirm;
    known-good component swapping is too costly/time-consuming as a
    primary method

### 4.3.4 — Troubleshoot Performance Issues

Structured order: check overheating/throttling → check misconfigurations
(esp. after recent changes) → verify/isolate via diagnostics → rule out
software/config/network causes.

- Recent build/upgrade/maintenance → check component compatibility; a
    memory upgrade can accidentally break dual-channel mode

- Standing diagnostic question: 'What has changed?'

- Diagnostics should isolate compute vs storage vs networking —
    compare against known baselines, quantify 'sluggish'

- Bottleneck = weakest component limits whole-system performance
    regardless of other strong specs (classic: fast CPU + HDD = still
    sluggish)

- Modern bottlenecks: NVMe misconfiguration, latency, PCIe
    lane/bandwidth mismatch (e.g., PCIe 3.0 vs 4.0)

- Rule out software/config BEFORE assuming hardware — e.g., a slow
    login script mimicking 'slow computer'

### 4.3.5 — Troubleshoot Inaccurate System Date/Time

Wrong system date/time disrupts network authentication and scheduled
tasks (backups, etc.).

- RTC = component tracking date/time; powered by a CR2032 coin-cell
    battery when the system is off

- Time wrong in system setup itself → likely failing RTC battery →
    replace with same type

- 'CMOS battery' = legacy name; modern systems use NVRAM/flash for
    config data — battery today mainly just sustains the RTC

- NTP = modern systems auto-sync time over the network, reducing
    reliance on RTC battery accuracy day-to-day

### 4.3.6 — Troubleshoot Missing Video Issues

- No image: check power/standby first → then input source (via OSD
    menu)

- Cabling: check both ends secure, not damaged; confirm cable spec
    matches use case (e.g., High-Speed HDMI for 4K)

- Rule out cable fault: swap in a known-good cable, OR test the
    monitor on a different PC to isolate display vs source

- Projectors use CRT/LCD/DLP + high-intensity bulbs (vs monitor
    backlights/LEDs)

- Failing bulb signs: dimming, bulb health warning; burnt-out bulb:
    popping sound, scorch marks, broken filament

- ⚠ Let a projector fully cool before handling/replacing the bulb

- Intermittent projector shutdown → overheating is the #1 suspect
    (fan, vents/dust, ambient temp); if not, check loose cables, bulb
    seating, firmware updates

### 4.3.7 — Troubleshoot Video Quality Issues

- Dim → check OSD brightness/power-saving features first; unresponsive
    dimness = backlight failure

- Fuzzy → resolution mismatch (output vs native) → fix in OS display
    settings or update driver

- Flashing → check cable first; could be backlight/circuitry OR
    overheating/faulty video card → isolate with a different PC

- Stuck pixel = sometimes fixable (cycling software, gentle tap); dead
    pixel = usually not repairable, check warranty

- Burn-in = static image too long; OLED/plasma more prone than TFT/LED
    (self-illuminating pixels vs shared backlight); prevent with
    screensaver or auto-off

- Color calibration = Color Management applet (Control Panel) + test
    patterns + spectrophotometer; gamma = RGB input vs light output
    relationship

- Color glitches (colored lines/shifts) → try cable replacement first
    → persists = monitor/GPU hardware fault

- Audio: HDMI/DisplayPort carry audio; DVI/VGA do NOT

- Sizing issues → match native resolution, use OSD to fit, update
    video drivers

- Distortion/warping → check interference, cable connections,
    resolution match; CRT = pincushion adjustment + check cable

### 4.3.8 — Real-World Video Troubleshooting (Industry Interview)

- #1 real-world video issue = loose/incorrect connection, not hardware
    failure — 'has this worked before?' is a fast diagnostic

- Docking stations: unplug/replug the dock from the PC, not each
    individual peripheral

- VGA/DVI = screw-secured, sturdier; HDMI/DisplayPort = no lock
    mechanism, loosens more easily

- After ruling out physical connection: check driver/firmware/OS
    updates next

- Driver reinstall = ~5 min fix vs ~24 hrs for a full setup
    replacement — always try the fast fix first

- Uninstall old driver BEFORE installing a new one; Display Driver
    Uninstaller (DDU) = clean-slate tool for graphics driver resets

- OLED burn-in = resurfacing modern issue, same root cause as legacy
    displays — fix = screen saver, avoid static 24/7 images

## 4.6 — Additional Resources

### 4.6.1 — BIOS and UEFI (recap)

- BIOS's 2.2TB drive limit exists specifically because of MBR's
    addressing limits

- UEFI's GPT support is what unlocks booting from drives larger than
    2.2TB

### 4.6.2 — Troubleshooting Example: Video Issues (worked case study)

Formal troubleshooting methodology demonstrated: Identify problem →
establish theory → test theory (repeat if disproven) → escalate/research
if direct testing fails → plan of action → implement fix → verify FULL
functionality (not just the original symptom) → document.

- Video failure points: cables (simplest fix), video card (onboard vs
    expansion, missing power connector), monitor (backlight failure =
    ghost image, internal PSU), drivers (variable quality by vendor),
    external cable surge/lightning exposure

- A disproven theory isn't a failure — it's expected; move to the
    next theory

- Vendor websites/documentation can reveal known compatibility issues
    not obvious from generic troubleshooting

- Always verify a fix against broader system use, not just the one
    symptom that triggered the ticket

- Documentation (both from the user and in a ticketing system) speeds
    up all future troubleshooting

**Quiz & Review Key Takeaways (4.1.11, 4.2.14, 4.3.10, 4.7, 4.8)**

- Boot order issues → always fix in boot option sequence, not by
    disabling/disconnecting hardware

- Secure Boot ≠ TPM: Secure Boot blocks untrusted bootloaders at boot;
    TPM generates/stores keys + verifies hashes

- Unsigned OS (e.g., fresh Linux install) blocked by Secure Boot →
    disable Secure Boot to allow it to boot

- HSM = TPM's portable alternative when TPM isn't supported — not
    a performance or backup tool

- 'Quiet' fan mode = reduced speed, higher tolerated temps ≠
    'Fanless' (no active cooling at all)

- Can't access RAID config utility at all = controller failure (not
    'array missing,' which means too many disks failed relative to
    RAID tolerance)

- 'No Bootable Device' → check boot order first, before
    cables/diagnostics/reinstall

- BSOD hex codes → check event logs matching that subsystem (e.g.,
    NTFS code → disk logs)

- Clicking/grinding noise = mechanical HDD failure signature →
    replace + restore from backup, not defrag/malware scan

- New hardware not detected → check what you just touched
    (connectors/seating) before escalating to PSU/motherboard
    replacement

- No power at all (LEDs off, fans silent) → test wall socket before
    any internal component work

- Gradual worsening over time (not sudden, not random) = classic
    dust/thermal buildup signature

- PSU stability = confirmed via multimeter voltage measurement, not
    visual inspection alone

- 'No signal' (projector/monitor) = cable/connection issue;
    blank/dim with power on = bulb/backlight issue

- Post-upgrade sluggishness → check the specific thing that changed
    (dual-channel mode, SSD config) before broader diagnostics

- Auth failures on a connected-but-unauthenticated system → check
    date/time sync, not cabling/disk/overheating

- CPU premature failure → ESD is the common culprit, not heat (thermal
    protection exists) or magnetism

- Post-CPU-upgrade shutdown after ~15 min → always check fan power +
    thermal paste application first

- USB 2.0 = 480 Mbps max (vs USB 1.1's 12 Mbps)

- SD card capacities: SD ≤2GB, SDHC ≤32GB, SDXC ≤2TB

- Optical drive stuck/won't eject → try the manual eject pinhole
    (paper clip) first

- Servers commonly use redundant, hot-swappable PSUs

- Full troubleshooting sequence: gather info/identify changes → form
    hypothesis → test → implement fix → back up before implementing when
    data is at risk → test solution → document

- RAID failure analysis should include root-cause investigation
    (controller logs), not just replacing the failed drive
