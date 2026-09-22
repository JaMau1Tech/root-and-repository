# Module 4 Objectives — In-Depth

*Troubleshooting PC Hardware — CompTIA A+ Core 1 (220-1201)*

## 3.5 — Given a scenario, install and configure motherboards, CPUs, and
add-on cards

Firmware is code stored in flash memory that initializes hardware before
the operating system loads. BIOS is the legacy standard — text-based,
keyboard-only navigation. UEFI is its modern replacement, adding a
graphical interface with mouse support, 64-bit operation, network boot
capability, and stronger boot security, while still able to fall back to
legacy BIOS mode when needed. Accessing setup requires pressing a
vendor-specific key (Esc, Del, F1, F2, F10, or F12) during the boot logo
screen; if that window is missed, modern systems boot fast enough that
the more reliable method is Shift-clicking Restart from the Windows
logon screen, which routes directly into UEFI boot options.

Boot device priority is the order firmware searches devices for a
bootable OS. Fixed disks connect via SATA (best practice:
lowest-numbered port for the boot drive) or the faster NVMe standard
over M.2/PCIe. Optical drives are only bumped to top priority
temporarily for installs or repairs from disc. USB drives need to be
specifically formatted as bootable. Network/PXE boot retrieves boot
instructions from a configured server over the network adapter, common
for enterprise imaging. Whenever a system boots from the wrong device,
the fix is almost always correcting this boot order rather than touching
hardware.

USB permissions in firmware allow enabling or disabling individual ports
or all USB ports as a security measure against unauthorized devices,
malware introduction, and data exfiltration — critically, this control
operates below the OS level, so it can't be bypassed by software
running on top of it. Fan behavior is also configurable in firmware,
with presets ranging from Balanced (general use) to Cool (maximum
airflow, more noise) to Quiet (less noise, higher tolerated temps) to
Fanless (passive only) to Custom (manual control), alongside a
minimum-temperature threshold and a duty-cycle percentage that directly
controls fan speed.

Boot security in UEFI includes two distinct password types: a
Supervisor/Setup password restricts access to the firmware setup program
itself, while a User/System password locks the entire system pre-boot
— but since this password must be shared with everyone who uses the
machine, it meaningfully weakens security and is really only appropriate
for machines with no interactive logon, like dedicated monitoring
servers. Secure Boot is UEFI's flagship security feature: it verifies
the OS bootloader against pre-loaded cryptographic keys (Microsoft, and
several major Linux distributions ship pre-loaded by default) before
allowing it to run, blocking anything modified or unsigned — which is
exactly why installing a fresh, unsigned Linux bootloader sometimes
requires disabling Secure Boot first.

The Trusted Platform Module (TPM) is a dedicated hardware chip that
securely stores digital certificates, cryptographic keys, and hashed
passwords, anchored by a unique, unchangeable endorsement key that
establishes a hardware root of trust. During boot, TPM compares hashes
of the firmware, bootloader, and OS kernel against known-good values to
detect tampering — any single-bit change anywhere in those components
produces a completely different hash, making tampering immediately and
unmistakably detectable. Because TPM keys live in tamper-resistant
hardware isolated from the OS and applications, they're far harder to
extract or compromise than keys stored in an ordinary file, which is
exactly why Windows BitLocker relies on TPM for its encryption keys. An
HSM (Hardware Security Module) — typically a secure, authenticated USB
device — serves as a portable alternative or backup to TPM when a
machine lacks TPM support, when the TPM chip itself is damaged, or when
an encrypted disk needs to move to a different computer.

## 5.1 — Given a scenario, troubleshoot motherboards, RAM, CPU, and power

When a PC powers on, the PSU converts AC to DC in a specific sequence:
12V arrives first (spinning up fans and disks), then the PSU tests its
5V and 3.3V supplies, and only once everything is stable does it send a
'power good' signal to the CPU authorizing it to start. Diagnosing a
total power failure starts with the simplest observable signs — are
front-panel LEDs lit, are fans audible — then works outward in a
specific isolation order: confirm other equipment in the area is working
(ruling out a circuit fault or blackout), test the wall socket with a
known-good device like a lamp, verify the PSU's own connections and
switch position, try a different power cable or check its fuse,
disconnect non-essential internal devices to rule out an underpowered
PSU or a single faulty component, and finally test the PSU directly with
a multimeter or dedicated tester if it's safe to do so. PSUs are never
user-serviceable internally — never remove the cover — and if a bad
PSU is suspected, it should never be left powered on unattended, with
immediate shutdown if smoke, unusual smells, or noises appear.

Once power is confirmed, POST (Power-On Self-Test) runs as a firmware
diagnostic checking required hardware before the OS loads; modern
systems run this so fast that a logo screen is shown instead of visible
messages, with detailed output only appearing on error. If a system has
power (fans spinning) but shows a blank screen with no beeps, the
troubleshooting sequence is: ask what changed recently (a failed
firmware update is a common culprit), attempt a reset, check that all
cabling and adapter cards are correctly seated (a misoriented cable or
loose card can silently halt POST), isolate a faulty device by removing
components one at a time, and check the PSU again — fans spinning
doesn't guarantee the 'power good' signal was actually sent, so POST
can still fail at this stage even with visible fan activity.
Misconfigured jumpers after recent service are another possible silent
culprit. When POST detects a problem severe enough to prevent any
display output, it communicates via manufacturer-specific beep codes
(interpretation always requires checking vendor documentation), though a
rough general reference includes: no beep suggesting a PSU, motherboard,
or speaker fault; a continuous beep suggesting memory or
memory-controller trouble; one long plus two or three short beeps
suggesting a video adapter error; and three long beeps suggesting a
stuck key on the keyboard.

Beyond the boot sequence, general component troubleshooting for lockups,
random shutdowns, or crashes should start by ruling out software, file
corruption, and malware before assuming hardware — these non-hardware
causes are actually more common. A pattern where errors appear only
after the system has been running a while strongly suggests a thermal
issue rather than a random fault. When hardware itself is suspected,
vendor diagnostic tools (often run from firmware rather than the OS,
since a failing OS may be too unstable to trust its own diagnostics) or,
absent those tools, physical/visual inspection are the next steps.
Practically speaking, RAM needs firm, even pressure on both sides to
seat correctly — most 'failure to POST after a RAM install' issues
are actually installation problems, not dead sticks — while a CPU
needs essentially no force at all to seat; any real resistance means
something is misaligned and needs to be rechecked before ever attaching
a heat sink, since a bent-pin CPU under an already-mounted heat sink is
a genuinely painful repair.

Overheating is diagnosed through several converging signals: a system
that's hot to the touch, temperature sensor readings compared against
vendor-specified limits, and physical checks of the CPU fan (is the
power cable connected, is it jammed or clogged, or — after a CPU
upgrade — is it simply undersized for the new chip's thermal output).
The heat sink itself should sit snug against the processor with fresh
thermal paste, since old paste degrades over time and needs periodic
renewal, not a single lifetime application. Blanking plates should cover
any unused holes in the case, since open holes disrupt the case's
intended, directional airflow path. Environmental factors matter too —
room temperature, dust levels, and whether the PC sits near a radiator
or in direct sunlight. A burning smell or visible smoke is treated as an
immediate, non-negotiable shutdown situation, most likely originating
from the power supply, though dust-clogged vents can also produce a
burning smell without any actual component failure. Left unaddressed,
thermal stress can cause secondary damage over time: connectors working
loose, components shifting in their sockets, and hairline circuit board
cracks widening — some of which are detectable through simple visual
inspection.

Physical damage most commonly affects the most exposed, frequently
handled parts of a system — peripherals, ports, and cables — with
internal damage more likely following transit; even a small crack or
dent in the case can signal a fall or knock that caused hidden internal
damage. On the motherboard specifically, damage can stem from ESD,
electrical spikes, or overheating affecting soldered components;
careless insertion bending pins on connectors; or 'chip creep,' where
an adapter gradually works loose from its socket purely from repeated
thermal expansion and contraction cycles over time, with no single
triggering event. Visible warning signs include liquid spill damage,
scorch marks from a 'blown' component, and swollen or bulging
capacitors, which regulate electrical flow and can indicate either
damage or a manufacturing defect. When motherboard damage is suspected,
diagnostic software is used to actually confirm the fault, since
swapping in known-good components one at a time is often too costly and
time-consuming as a primary diagnostic method — investigating recent
environmental changes or maintenance work as the likely root cause is
generally more efficient.

Performance troubleshooting follows a structured order: first rule out
overheating-driven throttling by checking temperature sensors and fan
speeds; then check for misconfigurations, especially right after a
recent build, upgrade, or maintenance event — the standing diagnostic
question here is always 'what has changed?' A classic example is a
memory upgrade that accidentally disables dual-channel mode by using
mismatched or improperly paired modules, quietly cutting bandwidth in
half. From there, verify the actual problem using diagnostic tests that
compare CPU, memory, disk, and network performance against known
baselines, isolating which specific subsystem — compute, storage, or
networking — is actually underperforming rather than treating
'sluggish' as one vague symptom. A bottleneck occurs when one weak
component drags down overall system performance regardless of how strong
everything else is — the classic example being a fast CPU and ample
RAM still feeling sluggish because the system is running an HDD instead
of an SSD — and even modern all-SSD systems can bottleneck through
improper NVMe configuration, latency issues, or a PCIe lane-speed
mismatch (for instance, a drive rated for PCIe 4.0 installed in a slot
that only runs at 3.0 speeds). Finally, software, configuration, and
networking causes need to be ruled out before assuming hardware is at
fault at all — a classic trap is a computer that 'feels slow' purely
because of a faulty network login script, with the hardware itself
performing completely normally.

Accurate system date and time matter more than they first appear, since
incorrect time can silently disrupt network authentication protocols and
make scheduled tasks like backups unreliable. The Real-Time Clock (RTC)
tracks date and time using a small CR2032 coin-cell battery specifically
to keep running while the system itself is powered off. If the time is
wrong within firmware setup itself (not just within the OS), a failing
RTC battery is the prime suspect and should be replaced with the same
battery type. This component is still commonly called the 'CMOS
battery,' a holdover name from when older systems stored their
configuration in CMOS RAM; modern systems instead store configuration in
NVRAM or flash memory, so today the battery's real job is narrower —
mainly just keeping the RTC itself running. Modern systems also commonly
use NTP (Network Time Protocol) to automatically resync time over the
network, which reduces day-to-day reliance on RTC battery accuracy,
though a dead battery can still cause issues at boot or when the system
is offline.

## 5.2 — Given a scenario, troubleshoot drive and RAID issues

After POST completes, the system checks boot devices in the configured
order; if the first isn't found, it tries the next, and if nothing
bootable is found at all, boot halts with an error. A system booting
from the wrong device usually means either interfering removable media
(a USB drive or disc left in) or a genuinely misconfigured boot order
that needs correcting. When a fixed disk isn't detected at all during
boot, work through a layered checklist: power (is there an activity LED,
can you hear it spin up, is the power connector secure), data
connections (inspect the cable for damage, confirm both ends are
properly seated), UEFI/BIOS settings (is the drive enabled, is SATA mode
set correctly to AHCI versus RAID), and for M.2/NVMe drives
specifically, confirm the drive is properly seated in its slot and
actually detected by firmware — moving through physical and electrical
checks before ever touching firmware configuration settings avoids
wasting time reconfiguring something that was really just a loose cable.

Once power and cabling are fully ruled out, boot sector and file system
corruption become the next suspects, with causes ranging from disk
faults and power failures to a botched multi-OS install or malware. The
two boot information formats are MBR (Master Boot Record) — a legacy
scheme confined entirely to the disk's first sector, supporting only
one active primary partition, making it a single point of failure, and
using BCD for Windows or GRUB/LILO for Linux as its boot managers —
and GPT (GUID Partition Table), the modern scheme that isn't limited to
a single sector and offers meaningfully more robust, flexible, and
reliable partition and bootloader identification. Corruption in either
scheme tends to produce specific, recognizable errors: 'Boot device not
found,' 'OS not found,' or 'Invalid drive specification.' It's
worth remembering that a blank screen during boot doesn't automatically
mean boot sector trouble — checking the display cable and connection
first is essential, since the two problems can look identical from the
outside. When malware is the suspected cause, an antivirus boot disk
provides both a scanner and dedicated tools to repair the boot sector;
absent that, the OS installation media's built-in repair options are
the fallback.

HDDs and SSDs fail through fundamentally different mechanisms — HDDs
are mechanical and tend to fail either early (manufacturing defects) or
late (accumulated wear), while SSDs have no moving parts but face a hard
limit on write cycles to their flash memory cells; power loss during any
write operation risks corruption or damage on either type. Recognizable
failure symptoms include unusual grinding, clicking, or scraping noise
(an HDD-exclusive mechanical signature, since SSDs have nothing to make
that sound), no LED activity (a power or connection problem for a single
drive, or a missing/failed array in a RAID context), constant
unrelenting LED activity ('disk thrashing,' which can mean
insufficient RAM forcing excessive paging, a runaway software process,
malware, or the disk itself failing), 'bootable device not found'
errors (file corruption, a faulty drive, or a RAID controller failing to
detect one or more array members), a drive missing entirely from the OS
(first check whether it's simply uninitialized/unpartitioned; if it's
not detected at all even in Disk Management, suspect hardware or
cabling), read/write failures like 'cannot read from the source disk'
(indicating bad sectors on an HDD or bad blocks on an SSD, diagnosable
and trackable via chkdsk, where an increasing bad-sector count signals
imminent failure), audible alarms on enterprise drives and RAID
controllers, and even a BSOD, since severe drive corruption or
persistent read/write errors can trigger a full system crash. Any of
these symptoms warrant an immediate backup and drive replacement rather
than waiting for further confirmation.

S.M.A.R.T. (Self-Monitoring, Analysis, and Reporting Technology) is a
built-in disk self-diagnostic capable of proactively alerting the OS to
failure before it happens. Advanced diagnostics — run through vendor
utilities, bundled system diagnostic tools, or Windows/third-party SMART
readers — report both physical damage and performance statistics like
IOPS (input/output operations per second). If measured performance falls
meaningfully below the manufacturer's baseline, the drive itself is
likely faulty; if performance matches the baseline, a 'slow' drive
complaint is probably really caused by something else entirely — heavy
application load, file fragmentation (an HDD-only concern), or simply
low remaining free space. Extended read/write times specifically trace
back to bad sectors (HDD) or bad blocks (SSD), which firmware marks
unusable once detected to prevent writing new data into a known-bad
location; file recovery is often possible from a failing HDD but is
generally not realistically possible from an SSD without highly
specialized tools, a meaningful practical difference between the two
drive types.

RAID protects against single-disk failure through mirroring or parity,
presenting the underlying disks to the OS as one unified volume. A
single device failure within a RAID array shows as a 'degraded' volume
— data remains accessible and the array typically still functions as a
boot device if configured that way — with the crucial exception of
RAID 0, which has zero redundancy at all: a single lost disk in RAID 0
takes down the entire volume, since RAID 0 exists purely to boost speed,
not reliability. Most desktop-level RAID implementations can only
tolerate the loss of one disk, so a failed drive should be replaced as
soon as possible; if the array supports hot swapping, a new disk can be
inserted directly, and the array then rebuilt through the RAID
configuration utility (hardware RAID) or an OS-level utility (software
RAID) — a process that temporarily and significantly impacts
performance, since the controller has to write potentially many
gigabytes of data onto the fresh disk. Never hot-swap a healthy disk by
mistake; a failing disk is typically flagged by a red LED, and data
should always be backed up before any hot-swap operation regardless of
confidence in the process. When an entire RAID volume goes missing or
shows unavailable, this means either more disks have failed than the
array's redundancy level can tolerate, or the RAID controller itself
has failed — if this affects the boot volume specifically, the OS
won't start at all, and recovery falls back to the latest backup or
file recovery tools. A failed controller (distinct from failed disks)
usually still leaves the underlying data recoverable, though possible
file corruption can occur if a write was interrupted mid-operation when
the controller died; the fix is installing a replacement controller or
importing the disks into a different system that can read the array. A
telling diagnostic sign: being completely unable to access the RAID
configuration utility at all strongly points to controller failure
specifically, as distinct from a simple 'array missing' message, which
instead points to too many failed disks.

## 5.3 — Given a scenario, troubleshoot video, projector, and display
issues

When no image appears on a display, the troubleshooting order starts
with the basics: confirm the display is powered on and not simply in
standby (try a key press or power cycle), then check the input source
through the monitor's own on-screen display (OSD) menu — an incorrect
input source, such as the monitor set to an empty DVI port while the
computer is actually connected via HDMI, is an extremely common and
easily overlooked cause. Once power and input source are ruled out,
examine the physical cable: is it securely connected at both ends and
free of damage, and does its specification actually match the use case
(a basic HDMI cable, for instance, may not support 4K, which requires a
High-Speed rated cable)? Newer standards like HDMI 2.1, DisplayPort 1.4,
and USB-C add further cable/port compatibility considerations beyond
simple connectivity. The reliable way to isolate a cable fault is the
'known good' substitution technique — swap in a cable you know
works, or test the monitor against an entirely different computer, which
cleanly separates a display-side fault from a source-side fault.

Beyond simple 'no image,' specific video quality symptoms each point
toward a particular cause. A dim image often traces back to OSD
brightness/contrast settings or an automatic power-saving feature
(adaptive brightness, eye-saving mode) reacting to ambient light or time
of day; if adjusting these doesn't help, a failed backlight is the
likely culprit and typically means the display needs repair. A fuzzy
image usually comes from a mismatch between the video card's output
resolution and the display's actual native resolution, fixed by
correcting the OS display settings or updating the video driver. A
flashing or flickering screen should prompt a cable check first, but can
also stem from a failing backlight or internal circuitry, or — less
obviously — an overheating or faulty video card itself, which is best
isolated by testing the monitor on a different computer. Dead and stuck
pixels behave differently: a stuck pixel (constantly lit) is sometimes
fixable with pixel-cycling software or a gentle tap, while a genuinely
dead pixel (black) usually cannot be repaired, making a warranty claim
the only real option. Display burn-in results from a static image
displayed for too long; OLED and plasma panels are meaningfully more
prone to this than TFT/LED because each OLED pixel self-illuminates
individually and ages based on its own usage, whereas TFT/LED panels
share a single backlight that ages more uniformly — prevention is
simply a screen saver or the display's built-in auto-off during
inactivity.

Color accuracy, especially relevant for digital art and print
production, is addressed through formal calibration using Windows'
Color Management applet alongside test card color patterns and, for
precise professional work, a spectrophotometer, together defining and
verifying a color profile. Gamma specifically describes the relationship
between the RGB values sent to a display and the actual light it emits,
with calibration tools guiding the adjustment toward neither too dark
nor too washed-out. Separate from calibration, color glitches —
unexpected colored lines or sudden color shifts — usually trace back
to a faulty or low-quality cable or a loose connector, worth ruling out
with a cable swap before suspecting a genuine hardware fault in the
monitor or graphics adapter. On the audio side, it's worth remembering
that HDMI and DisplayPort both carry audio alongside video, while DVI
and VGA carry video only — so 'no sound' over a DVI or VGA
connection isn't a fault at all, just the expected behavior of that
connector type; when audio genuinely should be present and isn't, check
power, physical connections, and confirm the correct audio output device
and volume level are actually selected in the OS. Sizing issues (a
stretched, compressed, or letterboxed image) are resolved by matching
the OS display resolution to the monitor's actual native resolution and
using the OSD to fit the image properly, alongside confirming video
drivers are current. Geometric distortion or a wavy image can stem from
nearby electronic interference, a loose cable connection, or a
resolution mismatch; on legacy CRT displays specifically, a
pincushion-shaped distortion has its own dedicated adjustment setting,
alongside checking for a simply faulty cable.

Projectors introduce their own specific failure modes on top of
everything above. Traditional projector technologies (CRT, LCD, DLP)
rely on a high-intensity bulb rather than the backlight or LED array
used in flat-panel monitors, and that bulb has a genuinely limited
lifespan. A failing bulb shows up as a dimming image, sometimes paired
with an explicit bulb-health warning from the projector itself; a fully
failed 'burnt-out' bulb can produce an audible pop along with visible
scorch marks or a broken filament. Because these bulbs run extremely hot
and become physically fragile while heated, a projector must be allowed
to fully cool down before anyone attempts to handle or replace the bulb.
Newer projectors increasingly use LED or laser light sources instead of
traditional bulbs, which last dramatically longer and are steadily
making 'burnt-out bulb' failures rarer on current-generation hardware.
Intermittent projector shutdowns are overwhelmingly caused by
overheating as the number one suspect — check that the fan is actually
running, that vents are clear of dust and debris, and that ambient room
temperature falls within the projector's rated operating range. If
overheating genuinely isn't the cause, check for loose connector cables
disrupting power or signal, confirm the bulb itself is fully and
securely seated (a loose bulb can itself trigger unexpected shutdowns),
and check for available firmware updates, since some shutdown issues are
purely software-related and resolved that way rather than through any
hardware fix.

Learning Outcomes by Lesson

Lesson 4.1 — BIOS and UEFI

**How can you access the UEFI setup program if you miss the key prompt
during the boot process?**

From the Windows logon screen, hold Shift and click Restart — this
routes into UEFI boot options directly, without depending on catching a
fast-moving key prompt during boot.

**What should you check if a computer is not booting from the correct
device?**

Check and correct the boot device priority/order in firmware setup —
confirm the intended drive is listed first and that no unintended
bootable media (a USB drive or disc) is set ahead of it or left
physically connected.

**How can you adjust the cooling settings in the system setup program?**

Under the Cooling, Power, or Advanced menu in firmware, select a preset
(Balanced, Cool, Quiet, Fanless) or choose Custom for manual fan speed
control, and set the minimum temperature threshold or duty cycle
percentage as needed.

**What is the purpose of Secure Boot in UEFI?**

Secure Boot prevents malware from hijacking the boot process by only
allowing digitally signed, trusted bootloaders to run, verifying each
one against pre-loaded cryptographic keys and blocking anything modified
or unsigned.

**What is the role of a Trusted Platform Module (TPM) in a computer
system?**

TPM provides a hardware-based root of trust: it securely stores
cryptographic keys and certificates in tamper-resistant hardware
isolated from the OS, and verifies system integrity at boot by checking
hashes of the firmware, bootloader, and OS kernel against known-good
values, both preventing key extraction and detecting tampering.

Lesson 4.2 — Power and Disk Issues

**What steps would you take to diagnose a computer that won't start due
to a power issue?**

Check LEDs and listen for fans first, then work through the isolation
sequence: other equipment in the area, the wall socket, PSU connections,
the power cable/fuse, disconnecting extra devices, and finally testing
the PSU directly with a multimeter — all while following PSU safety
precautions.

**What should you do if the computer powers on but does not start,
showing a black screen with no beeps?**

Ask what has changed recently (a failed firmware update is common), try
a reset, check cabling and adapter card seating, isolate a faulty device
by removing components one at a time, check the PSU's power-good
signal, and check for jumper misconfiguration or a CPU/firmware fault.

**What should you check if a fixed disk is not detected during boot?**

Check power delivery (activity LED, spin-up sound, secure connector),
inspect and reseat the data cable, confirm the drive is enabled in
UEFI/BIOS with the correct SATA mode, and for M.2/NVMe drives
specifically, confirm proper seating and firmware detection.

**What are the two ways of formatting boot information, and how do they
differ?**

MBR (Master Boot Record) is the legacy scheme, confined to the disk's
first sector with only one bootable primary partition allowed, making it
a single point of failure. GPT (GUID Partition Table) is the modern
scheme, not limited to a single sector, offering more robust, flexible,
and reliable partitioning and bootloader identification.

**What should you do if a Windows system displays a blue screen of death
(BSOD)?**

Scan the QR code on the crash screen for details, check the System
log's 'BugCheck' entry and search the first hex error code online,
and if under a support contract, use the automatically generated memory
dump for deeper analysis — keeping in mind causes range from driver
issues to overheating or power problems.

**What are common symptoms of a failing hard disk drive (HDD)?**

Unusual grinding or clicking noise, no or constant LED activity,
'bootable device not found' errors, drives missing from the OS,
read/write failures with an increasing bad-sector count, audible
RAID/enterprise alarms, and BSOD crashes tied to drive corruption —
any of which should prompt an immediate backup and drive replacement.

Lesson 4.3 — System and Display Issues

**What steps should you take to diagnose intermittent system lockups and
shutdowns?**

Rule out software, file corruption, and malware first, then look for
patterns (errors appearing only after extended runtime suggest a thermal
issue), check PSU voltage stability, run vendor hardware diagnostics
(often via firmware), and fall back to physical inspection if no
diagnostic tools are available.

**How can you diagnose and correct overheating issues in a computer
system?**

Check temperature sensors against vendor limits, verify CPU fan function
(connected, unobstructed, adequately sized for the CPU), confirm the
heat sink is snug with fresh thermal paste, use blanking plates to
maintain proper case airflow, and rule out environmental factors like
room temperature or direct sunlight — treating any burning smell as an
immediate shutdown situation.

**What should you check if a computer is experiencing sluggish
performance after a new build or upgrade?**

Check for component compatibility issues introduced by the change itself
— for example, a memory upgrade that accidentally disabled
dual-channel mode — by asking 'what has changed?' and verifying the
new component's configuration against what the motherboard actually
supports.

**What steps would you take to troubleshoot a monitor that shows no
image?**

Check power and standby mode first, then check the input source via the
OSD menu, then check cabling, then substitute a known-good cable or test
the monitor on a different PC to isolate the fault.

**How can you rule out cable problems when troubleshooting a display
issue?**

Swap in a known-good cable, or test the display with a different PC —
the 'known good' substitution technique isolates whether the fault is
the cable, the display, or the source.

**What steps should you take to troubleshoot intermittent shutdowns in
projectors?**

Check for overheating first (fan function, clear vents/dust, ambient
temperature within range), then check for loose cables, improper bulb
seating, and available firmware updates if overheating isn't the cause.
