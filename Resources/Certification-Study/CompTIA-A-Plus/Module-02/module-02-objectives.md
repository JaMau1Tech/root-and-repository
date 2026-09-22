# Module 2 Objectives — In-Depth

*Installing Motherboards and Connectors — CompTIA A+ Core 1
(220-1201)*

Nearly the entire module lives in Domain 3.0 Hardware (25% of the exam).

## 3.1 — Compare and contrast display components and attributes

Displays break down into LCD subtypes, each with a different tradeoff:
IPS offers the best color accuracy, making it the choice for design
work; TN offers the fastest response time at the cost of weaker color,
making it popular for competitive gaming; VA sits in the middle with
especially strong contrast. Beyond LCD, OLED illuminates each pixel
individually, which produces true blacks but introduces a real risk of
burn-in from static images. Mini-LED is a backlit LCD design with far
more, much smaller backlight zones than older LCDs, which gets much of
OLED's contrast benefit without the burn-in risk.

Display components beyond the panel itself include touch screens (which
turn the display into an input device, not just output — unrelated to
resolution or power draw), inverters (which power older CCFL backlights,
now mostly legacy since most modern displays use LED backlighting), and
pixel resolution and refresh rate. A key exam-relevant idea: the cable
or connector itself can bottleneck image quality. A great monitor still
looks worse over a weak analog VGA connection than a good digital HDMI
or DisplayPort connection, because the cable is carrying a
lower-fidelity signal regardless of what the panel is capable of.

On the legacy side, VGA was the standard analog interface for CRT
monitors and projectors for many years. It uses a 15-pin, D-shell
connector secured with screws (one of the only common video connectors
designed to bolt in rather than just friction-fit, useful for older CRT
setups that got bumped around). VGA tops out realistically around Full
HD (1920x1080) and carries video only — no audio. DVI offered a step
up by supporting digital signaling, but came in confusingly many
variants: DVI-I supports both analog and digital, DVI-A supports analog
only, and DVI-D supports digital only, each with different physical pin
layouts that are not interchangeable. Both DVI-D and DVI-I also come in
single-link and dual-link versions, where dual-link provides extra
bandwidth for higher resolutions and refresh rates.

## 3.2 — Summarize basic cable types and their connectors, features, and
purposes

USB is the standard for connecting modern peripherals and carries both
power and data over 3m or 5m cable runs. USB-C is a connector shape, not
a speed standard — a USB-C port could be running anything from USB 2.0
to Thunderbolt underneath, so never assume speed from the connector's
physical shape alone. There is also no official color standard for USB
ports; blue for 3.x is a common convention, not a guarantee — check
documentation when it matters. USB standards roughly double in speed
with each generation: USB 1.0/1.1 runs at 1.5 or 12 Mbps, USB 2.0 at 480
Mbps, USB 3.0 at 5 Gbps, USB 3.1 at 10 Gbps, USB 3.2 variants at 5/10/20
Gbps, and USB 4.0 at 40 Gbps.

HDMI and DisplayPort both carry audio and video together. HDMI is the
dominant connector for monitors, TVs, and consoles, keyed well and
physically robust, and can even carry a network connection over the same
cable. DisplayPort looks similar but is visually distinguishable by its
connector shape — one cut edge versus HDMI's two — and uniquely
supports daisy chaining multiple displays off a single connector, along
with syncing video and audio precisely; it's popular with gamers and
graphic designers who need that multi-monitor flexibility.

Thunderbolt shares USB-C's physical connector shape starting at version
3, but delivers dramatically higher throughput (up to 40 Gbps for TB3/4)
and can carry a DisplayPort video signal and PCIe data simultaneously
over the same cable — think of it as USB-C's overachieving cousin.
Lightning is Apple's proprietary connector for iPhone/iPad, being
phased out in favor of USB-C due to an EU mandate requiring universal
charging standards across consumer electronics.

SATA is the standard interface for internal storage, replacing the
older, wider ribbon-cable PATA/IDE standard with a smaller, faster,
keyed connector. Each SATA revision roughly doubles the last: Rev 1 at
1.5 Gbps (150 MBps), Rev 2 at 3 Gbps (300 MBps), Rev 3 at 6 Gbps (600
MBps). SATA devices require two separate cables — a red-sleeved data
cable and a separate multicolored power cable — a real point of
failure worth checking first during troubleshooting, since SATA data
cables are known to work loose over time and vibration. eSATA is a
separate, better-shielded connector built for external use (up to 2
meters), and is not compatible with internal SATA cables; a key
limitation is that standard eSATA does not supply power over the cable,
unlike eSATAp, which combines eSATA and USB to add power delivery.

Molex is one of the oldest power connectors still in circulation, a
4-pin connector with a fixed, memorizable color code: red = 5 VDC,
yellow = 12 VDC, black = ground. It still appears on some fans, RGB
lighting, and older drive enclosures.

Legacy serial cabling (RS-232) transmits data one bit at a time over a
single wire, using start, stop, and parity bits to format and verify the
data. It's slow by modern standards — up to about 115 Kbps — which
is precisely why it's considered legacy: the limiting factor is raw
speed, not OS compatibility or connector size. RS-232 specifies a 25-pin
interface, but PCs typically use the cheaper 9-pin DB9 connector,
referred to in Windows as a Communications (COM) port. Serial ports were
once common for dial-up modems, a role USB has taken over, but serial
connections persist today specifically for configuring network equipment
like routers and switches via console cable. A related legacy connector,
PS/2, connects mice and keyboards via a 6-pin mini-DIN plug,
distinguished only by color since the ports are physically identical —
green for mouse, purple for keyboard.

Because so many connector types exist, adapter cables bridge the gap
between a PC port and a peripheral's port. The critical distinction is
active versus passive: an active adapter uses circuitry to convert the
signal itself between genuinely different protocols (for example,
digital HDMI into analog VGA), which is necessary whenever the two ends
speak different signaling languages. A passive adapter just converts
connector shape without touching the underlying signal, which works
whenever both ends already use the same signaling standard (for example,
USB-C to USB-A, where the data is identical, only the plug shape
differs).

## 3.3 — Compare and contrast RAM characteristics

On the motherboard, system memory slots take the form of DIMM sockets,
and RAM has gone through several incompatible generations — DDR2,
DDR3, DDR4, and DDR5 — each with a different notch position on the
module's edge connector. This is a physical safeguard, not just a spec
difference: a DDR4 module cannot be physically forced into a DDR3 slot,
because the notch simply won't align, preventing someone from
accidentally installing the wrong RAM generation and damaging the board
or the module.

## 3.4 — Compare and contrast storage devices

The motherboard offers several storage connector types. SATA remains the
most common, requiring both a data cable to a SATA port and a separate
power connector (SATA power or Molex) run to the power supply. M.2 is a
newer adapter-card form factor for SSDs, using a horizontally oriented
slot; the drive itself is inserted at an angle, then pushed flat and
secured with a single screw. M.2 drives come in standard lengths —
42mm, 60mm, 80mm, or 110mm — and must match what the specific
motherboard slot supports, which is usually printed on the board itself.
Unlike SATA, M.2 draws power directly over the bus, eliminating the need
for a separate power cable, which is a meaningful part of why M.2 has
become the default in modern laptops especially.

eSATA extends SATA outside the case with better shielding for longer,
more durable external runs, but is not power-capable in its standard
form (eSATAp solves this by combining USB power delivery with the eSATA
connector) — a limitation that contributed significantly to USB
winning out as the dominant external storage interface, since USB
carries both data and power in a single cable from the start.

On the legacy side, SCSI (Small Computer System Interface) was an older
storage interface, largely superseded today by SATA for consumer use and
SAS for enterprise/server use — SAS is essentially SCSI's modern
serial successor, the same relationship SATA has to old PATA/IDE. SCSI
devices are daisy-chained together on a single shared bus, unlike SATA
where each drive gets its own dedicated cable back to the motherboard.
Each device on a SCSI chain needs a unique ID for addressing — Narrow
SCSI supports IDs 0 through 7 (8 devices max), Wide SCSI supports IDs 0
through 15 (16 devices max). Critically, both physical ends of the SCSI
bus chain must be terminated, regardless of which device ID happens to
sit at that physical end — termination absorbs the signal so it
doesn't reflect back down the cable and corrupt data. This is a classic
exam trap: termination is about physical position on the chain (start or
end), not about which device ID is assigned there.

## 3.5 — Given a scenario, install and configure motherboards, CPUs, and
add-on cards

The motherboard's core function is providing data and power bus
connectivity between every other hardware component, with the system
clock providing timing that keeps everything synchronized — a useful
mental model is the motherboard as a nervous system and the CPU as the
brain, where every component's signal has to route through the
motherboard to reach the CPU. A bus, in this context, is simply a set of
wires letting two components communicate; bus width varies (4-bit,
8-bit, 128-bit, etc.) depending on the job, the same underlying concept
as PCIe lane counts below. Named buses include the memory bus (CPU to
RAM), the data bus (storage and other systems), and the video bus (video
card).

Before touching any board, electrical safety and ESD prevention come
first — grounding straps and mats, an electrically safe workbench, and
storing parts in ESD bags. This matters because a static discharge too
small to even feel can still permanently damage a chip like a CPU or RAM
module.

Expansion slots exist because early computers were built with fixed,
non-expandable hardware, and expansion buses were invented specifically
to let capability grow after the fact. PCIe is now the dominant
standard, using point-to-point serial communication so each component
gets a dedicated link rather than sharing a single parallel bus. Each
connection is called a link, built from one or more lanes (x1, x4, x8,
x16 — more lanes means more simultaneous throughput, just like more
highway lanes). The raw per-lane transfer rate is measured in GT/s
(giga-transfers per second), but the real usable throughput in GB/s is
lower, since some of the raw signal is spent on encoding overhead rather
than actual data — this is why a PCIe 3 x16 slot lists 8 GT/s raw but
only about 15.75 GB/s of real throughput. Cards and slots don't always
match lane-for-lane: up-plugging puts a card with fewer lanes into a
slot with more (it should run at its native lane count but can sometimes
fall back lower), while down-plugging fits a physically longer card into
a shorter, open-ended slot. All PCIe versions are backward-compatible,
but the link always runs at the speed of whichever component — card or
slot — is the older, lower version. PCIe also delivers power directly
through the slot (up to 75W via a dedicated graphics slot, up to 25W
elsewhere), with high-power cards drawing additional power through
separate 6/8-pin connectors straight from the PSU because the slot alone
often isn't enough for a 200-450W graphics card. A frequently
overlooked gotcha: slots that share a pool of lanes with other
components (another PCIe slot, or an M.2/NVMe slot) will divide
available bandwidth between them, so populating one slot can silently
slow another down — always check the motherboard's lane-sharing
diagram rather than assuming every slot runs independently at full
speed.

PCI is the legacy predecessor to PCIe, using parallel communication
instead of PCIe's serial approach — parallel sends many bits
side-by-side down multiple wires, which sounds faster on paper but runs
into signal crosstalk at high speeds that caps how far it can scale,
whereas serial's single fast lane has no such crosstalk problem and
scales much further, which is exactly why PCIe won out despite
'serial' sounding slower. PCI cards physically cannot fit PCIe slots,
though a PCIe motherboard can still carry separate physical PCI slots to
support legacy cards. PCI cards also use different keying (notch
position) depending on their voltage requirement — 5V, 3.3V, or
dual-voltage — a physical safety mechanism identical in concept to the
DDR RAM notch-keying already covered under 3.3.

Motherboard form factor defines shape, size, compatible case, compatible
power supply, and how many expansion slots the board offers. ATX is the
standard full desktop size at 12 by 9.6 inches with up to seven
expansion slots. Micro-ATX shrinks to a 9.6-inch square with up to four
slots, and typically still fits in an ATX case. Mini-ITX shrinks further
to 6.7 inches square with just one expansion slot, and can also mount in
larger ATX cases. Smaller boards generally fit into bigger cases, but
never the reverse — you cannot fit a full ATX board into a Mini-ITX
case.

Installing a motherboard follows a specific order for good reason:
review documentation and check jumper settings first (modern boards
increasingly handle this through BIOS/UEFI instead), install the I/O
shield, then insert standoffs that must precisely match the
motherboard's mounting holes — an extra standoff positioned under
bare board material with no matching hole can cause a direct short
circuit against the case. It's recommended to pre-install the CPU,
memory, and CPU cooler onto the board before mounting it in the case,
since you have full, unobstructed access to the socket before the case
walls get in the way. When securing the board, align it with the I/O
shield cutout (typically top-left), ensure standoffs support it at the
edges and center (not just the corners), and tighten screws firm but not
overtight — excessive force can flex and crack the board itself. Final
assembly connects the PSU, disk drives, and adapter cards, followed by
careful cable management to preserve airflow.

Beyond the sockets and slots, motherboards include headers for front and
rear panel components. The power button uses 'soft power' — a normal
press sends a signal the OS interprets as a shutdown request, while
holding it down for several seconds cuts power directly, bypassing the
OS entirely (a last resort for a frozen system, since nothing gets
saved). Drive activity LEDs connect via a header usually labeled 'HDD
LED.' Front-panel audio connects through an HD Audio header. USB
headers come in two forms: a 9-pin header for two USB 2 ports (the 9th
pin ensures correct cable orientation), and a 20-pin (2x10) header for
USB 3 at faster speeds. Because these small pin clusters look nearly
identical once disconnected and carry no visual indicator of correct
orientation, it's worth photographing or diagramming their positions
before disassembly. The main motherboard power connector, P1, is a
distinctive 24-pin block arranged in two rows of 12. Fan headers come in
two types: 3-pin headers control speed crudely by varying voltage (like
a dimmer switch), while 4-pin headers use PWM (pulse width modulation,
carried on the blue wire) for much finer speed control by rapidly
switching full power on and off and letting the fan respond to the
average. A 3-pin fan plugged into a 4-pin header will generally work but
without fine speed control, and a 4-pin fan plugged into a 3-pin header
will work but loses PWM control entirely.

Beyond the CPU itself, several expansion card types round out this
objective. Video cards contain a GPU plus dedicated graphics memory
(VRAM) that is separate from system RAM — the key distinction from
integrated graphics, which borrows a slice of system RAM instead.
Capture cards work in the opposite direction from a graphics card: where
a GPU pushes video output to a monitor, a capture card pulls video input
in from an external source (game consoles, camcorders, security cameras)
to record or stream it, available as internal PCIe cards (lower latency,
professional use) or external USB/Thunderbolt units (portable, easy
setup, casual or multi-device use). Sound cards use color-coded 3.5mm
jacks that are worth memorizing outright: green and black for audio out,
blue and pink for audio in (pink specifically for microphone), and
orange for a subwoofer out. Network interface cards connect via copper
(RJ-11 for phone/DSL, the visibly larger RJ-45 for Ethernet), coaxial,
fiber optic, or wireless.

Finally, this objective extends conceptually to CPU architecture choices
in a virtualization context: a server hosting several hundred virtual
machines needs a 64-bit (x64) processor rather than 32-bit x86, because
hosting that many VMs demands massive memory capacity that x64's
addressing space supports and 32-bit x86's roughly 4GB ceiling cannot.
x86/x64 platforms from Intel and AMD also carry the hardware
virtualization support (VT-x/AMD-V) that hypervisors depend on, while
ARM is optimized for performance-per-watt in mobile and embedded
contexts rather than the raw memory-capacity profile a large
virtualization host needs.

Learning Outcomes

**Explain cable types and connectors.**

This module covers the full range from modern to legacy: USB (all
generations and connector types), HDMI and DisplayPort, Thunderbolt,
Lightning, SATA and eSATA, Molex, VGA and DVI, serial (RS-232) and PS/2,
and adapter cables (active vs. passive). For each, the exam-relevant
details are the connector's physical distinguishing features, what it
carries (data, video, audio, power, or some combination), its typical
speed or resolution ceiling, and how to visually identify it at a glance
— the real-world skill being tested throughout is fast, confident
visual identification, not just definitions recited from memory.

**Install and configure motherboards.**

This spans motherboard functions and the bus system, ESD/electrical
safety, CPU and memory connectors, storage connectors (SATA, M.2,
eSATA), PCIe and legacy PCI expansion slots, motherboard form factors
(ATX, mATX, Mini-ITX), the full physical installation procedure in
order, and the headers/power connectors that tie front-panel components
and fans back to the board. The throughline is understanding the
motherboard as the central connection point every other component
depends on, and knowing the correct sequence and precautions for
physically installing one without damaging it.

**Explain legacy cable types.**

Legacy cable types — DVI, VGA, serial/RS-232, PS/2 — represent
earlier standards that modern connectors (HDMI, DisplayPort, USB) have
largely replaced, generally because the legacy standard hit a hard
ceiling on speed, resolution, or functionality (analog-only signaling,
no audio support, no power delivery) that the industry needed to move
past. Recognizing these legacy connectors, knowing what limitation
caused their replacement, and knowing what replaced them is the core
skill this section tests.
