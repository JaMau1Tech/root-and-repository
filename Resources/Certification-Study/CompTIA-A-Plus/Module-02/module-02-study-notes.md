# Module 2 Study Notes

*Installing Motherboards and Connectors — CompTIA A+ Core 1
(220-1201)*

Objectives covered: 3.1 (display components/attributes), 3.2 (cable
types/connectors), 3.3 (RAM characteristics), 3.4 (storage devices), 3.5
(motherboards/CPUs/add-on cards). Nearly the entire module lives in
Domain 3.0 Hardware (25% of the exam).

## 2.1 — Cables and Connectors

### 2.1.1 — Personal Computers

- Front of case: disk drives, power switch, LEDs, peripheral ports,
    intake air vents (keep clean)

- Rear of case: power plug, PSU, rear peripheral ports, expansion card
    access, exhaust vents (keep clean)

- Front vents pull cool air in; rear vents push hot air out —
    clogged vents break the whole airflow path

### 2.1.3 — Peripheral Devices

- Categories: Interfaces, Ports, Connectors

- Capital B = Byte (8 bits); lowercase b = bit

- Unit conversions: Kilo → Mega → Giga → Tera → Peta; be ready to
    convert Mbps → MBps (divide by 8)

- A '100 Mbps' connection only downloads at roughly 12.5 MB/s —
    this mismatch trips people up constantly

### 2.1.4 — Universal Serial Bus (USB) Cables

USB carries both power and data. Cable length: 3m or 5m. USB-C is a
connector SHAPE, not a speed — a USB-C port could run USB 2.0 or
Thunderbolt speeds underneath.

- USB 2.0 connectors: Type A, Type B, Type B Mini, Type B Micro

- USB 3.0/3.1 connectors: Type A, Type B, Type B Micro, Type C

- ⚠ No official color standard for USB ports (even though 3.x is often
    colored blue) — check documentation to confirm generation

### 2.1.5 — USB Standards (memorize this table)

- USB 1.0/1.1 — 1.5 Mbps or 12 Mbps

- USB 2.0 — 480 Mbps

- USB 3.0 — 5 Gbps

- USB 3.1 — 10 Gbps

- USB 3.2 Gen 1/2/2x2 — 5 Gbps / 10 Gbps / 20 Gbps

- USB 4.0 — 40 Gbps

- Each generation roughly doubles the last — know the order of
    magnitude, not every decimal

### 2.1.8 — Display Types

- LCD subtypes: IPS (best color accuracy, design work), TN (fastest
    response time, weaker color, gaming), VA (middle ground, strong
    contrast)

- OLED = each pixel self-illuminates (true blacks, burn-in risk);
    Mini-LED = backlit LCD with more/smaller backlight zones (better
    contrast, no burn-in risk)

### 2.1.9 — Display Components

- Touch screen, inverters (power older CCFL backlights, mostly
    legacy), pixel resolution and refresh rates

- The cable/connector can bottleneck image quality — compare VGA vs
    DP vs HDMI

- Touch screen turns the display itself into an input device —
    doesn't require external hardware, unrelated to resolution/power

### 2.1.10 — HDMI and DisplayPort

- Both carry audio + video

- HDMI: higher-quality resolutions/color/refresh rates depending on
    version; popular with general AV

- DisplayPort: professional-quality resolutions, high refresh rates;
    supports daisy chaining multiple displays off one connector; syncs
    video and audio; popular with gamers/graphic designers

### 2.1.11 — Thunderbolt Interface

- TB 1 & 2 — Mini-DP connector, up to 20 Gbps, daisy chaining
    supported

- TB 3 — USB-C connector, 40 Gbps, over 0.5m cable

- TB 4 — USB-C connector, 40 Gbps

- TB 5 — USB-C connector, high speed, built for future use

- Thunderbolt = same connector shape as USB-C (from v3+) but far
    higher throughput; can also carry DisplayPort video + PCIe data over
    the same cable

### 2.1.12 — Lightning Interface

- Apple proprietary connector for iPhone/iPad — being replaced by
    USB-C due to EU mandate

### 2.1.13 — SATA (Serial ATA)

- Standard for internal storage; smaller connector, faster than legacy
    PATA/IDE

- SATA Rev 1 — 1.5 Gbps (150 MBps); Rev 2 — 3 Gbps (300 MBps); Rev
    3 — 6 Gbps (600 MBps)

- Separate data cable (red sleeve) and power cable (multicolored
    wires)

### 2.1.14 — Molex Power Connectors

- 4-pin connector; wire colors: Red = 5 VDC, Yellow = 12 VDC, Black =
    Ground — classic exam trap

### 2.1.15 — External SATA (eSATA)

- Own eSATA connector; internal and external SATA cables are NOT
    compatible

- Max cable length: up to 2 meters

## 2.2 — Motherboards

### 2.2.1 — Motherboard Functions

- Provides data and power bus connectivity between hardware
    components; system clock provides timing

- Leading manufacturers: Acer, ASRock, ASUSTek, Biostar, Intel, MSI

### 2.2.2 — Electrical Safety and ESD

- Safety is always the priority — never work on energized equipment

- ESD prevention: grounding strap and mats, electrically safe
    workbench, store parts in ESD bags

- A static discharge too small to feel can still permanently damage a
    chip

### 2.2.3 — CPU and System Memory Connectors

- CPU socket; system memory slots = DIMM

- RAM generations: DDR2, DDR3, DDR4, DDR5 — NOT compatible with each
    other (different notch/pin layouts)

### 2.2.4 — Motherboard Storage Connectors

SATA: motherboard has several SATA ports for fixed drives, plus
removable drives (tape, optical). SATA devices need TWO cables — a
data cable to a SATA port, and a SATA power or Molex connector to the
PSU.

- M.2 Interface: horizontal port; adapter card inserted at an angle,
    pushed flat, secured with a screw; lengths 42/60/80/110mm must match
    motherboard support; supplies power over the bus — no separate
    power cable needed

- eSATA: better shielding for external use, up to 2m; eSATAp ('Power
    over eSATA') combines eSATA+USB and DOES provide power, unlike
    standard eSATA

- ⚠ Standard eSATA does not supply power over the cable — a real
    limitation for bus-powered 2.5" drives, part of why USB won the
    format war

### 2.2.5 — PCIe (Peripheral Component Interconnect Express)

PCIe is the standard interface for modern adapter cards —
point-to-point serial communication giving each component a dedicated
link.

- Each connection = a link, using one or more lanes; raw rate per lane
    = GT/s (giga-transfers/sec); real usable rate = GB/s (lower, due to
    encoding overhead)

- PCIe v2: 5 GT/s (0.5 GB/s x1, 8 GB/s x16); v3: 8 GT/s
    (0.985/15.754); v4: 16 GT/s (1.969/31.508); v5: 32 GT/s
    (3.938/63.015); v6: 64 GT/s (7.56/128)

- Up-plugging: fewer-lane card into a bigger slot (e.g., x8 card in
    x16 slot) — runs at native x8, may fall back to x1

- Down-plugging: physically longer card into a shorter open-ended slot
    — works only if the slot isn't obstructed

- ⚠ A slot may support fewer lanes than its physical size suggests —
    check the motherboard label (e.g., 'x16 @ x8')

- All PCIe versions are backward-compatible — the link runs at the
    speed of the LOWEST-version component in the pair

- Power: PCIe supplies up to 75W via a graphics adapter slot, up to
    25W through other slots; an additional 75W can come through a
    separate PCIe power connector (6/8-pin from PSU)

- ⚠ Shared bandwidth: slots sharing lanes with other components
    (another slot, or M.2/NVMe) divide total available bandwidth —
    populating one slot can silently reduce another's speed

- Lane widths: x1, x4, x8, x16 — more lanes = more simultaneous
    throughput (like highway lanes)

### 2.2.6 — PCI (legacy)

- Legacy bus, superseded by PCIe; PCIe is software-compatible with
    PCI, but PCI cards physically cannot fit into PCIe slots

- Uses parallel communication (vs PCIe's serial); typically 32-bit,
    33.3 MHz, up to 133 MBps

- Voltage: early PCI = 5V signaling; later 3.3V and dual-voltage
    became common; different keying (notch position) prevents
    wrong-voltage cards from being inserted

- Parallel sends many bits side-by-side (crosstalk limits speed at
    high rates); serial sends bits one after another down a single fast
    lane (scales much higher) — this is why PCIe replaced PCI despite
    'serial' sounding slower

### 2.2.7 — Motherboard Form Factors (memorize this table)

- ATX — 12" x 9.6" (305 x 244mm) — up to 7 expansion slots —
    standard for most desktops

- Micro-ATX (mATX) — 9.6" x 9.6" (244 x 244mm) — up to 4
    expansion slots — usually fits in ATX cases too

- Mini-ITX — 6.7" x 6.7" (170 x 170mm) — 1 expansion slot —
    can also mount in ATX cases

- Smaller nano-, pico-, mobile-ITX exist for embedded
    systems/portables, not standard PCs

- Smaller boards can go into bigger cases, never the reverse; slot
    count drops predictably: 7 → 4 → 1

### 2.2.8 — Motherboard Installation (steps)

- 1. Review documentation — check jumper settings (modern boards
    often use BIOS/UEFI instead); protect from ESD

- 2. Install the I/O shield — align with rear ports, snap into
    place

- 3. Insert standoffs — must match motherboard mounting holes
    exactly; an extra standoff under bare board material can
    short-circuit the board

- 4. Pre-install CPU, memory, and CPU cooler BEFORE securing the
    board — easier access, less damage risk

- 5. Align and secure the board — I/O shield cutout (usually
    top-left), standoffs at edges AND center, screws firm but not
    overtightened (overtightening can crack the board)

- 6. Final assembly — connect PSU, disk drives, adapter cards, all
    data/power connectors

- 7. Cable management — route cables to maintain airflow and
    prevent clutter

### 2.2.10 — Motherboard Headers and Power Connectors

Headers connect front/rear panel components to the motherboard.

- Power button (soft power) sends an OS shutdown signal; holding it a
    few seconds cuts power directly, bypassing the OS

- Drive (HDD) activity light header, usually labeled 'HDD LED'

- Audio: front-panel audio connects via an HD Audio header (or
    'AC'97' on older systems)

- USB 2 internal = 9-pin headers (up to two 4-pin ports, 9th pin
    ensures orientation); USB 3 internal = 20-pin (2x10) headers

- ⚠ Photograph/diagram header positions before disassembly — pin
    blocks look nearly identical once removed

- Main power connector (P1): 24-pin block (2 rows of 12), square pin
    receptacles

- 3-pin fan connector: voltage-based speed control (like a dimmer
    switch)

- 4-pin fan connector: PWM (pulse width modulation) speed control,
    signal on the blue wire — more precise than voltage control

- ⚠ 3-pin fan on 4-pin header = works, but may lack speed variation;
    4-pin fan on 3-pin header = works, but loses PWM control

### 2.2.12 — Video Cards

- Expansion card containing a GPU + dedicated graphics memory (VRAM)
    — separate from system RAM, unlike integrated graphics which
    borrows system RAM

- Multiple video ports: DisplayPort, HDMI, DVI-I, etc.

### 2.2.14 — Capture Cards

A graphics card outputs video to a monitor; a capture card records video
INPUT and saves/streams it — opposite data direction.

- Game Capture Cards — record/stream gameplay via HDMI

- HDMI Capture Cards — record from various HDMI sources (consoles,
    camcorders, security cams)

- TV Tuner Cards — receive/record broadcast TV

- Internal (PCIe) = lower latency, higher performance, professional
    use; External (USB/Thunderbolt) = portable, easy,
    casual/multi-device use

### 2.2.15 — Sound Cards (color-coded jacks)

- Green = Audio Out; Black = Audio Out; Blue = Audio In; Pink = Audio
    In (Microphone); Orange = Audio Out (Subwoofer)

- Memory trick: green = headphones/speakers, pink = mic — the two
    most common exam trip-ups

### 2.2.16 — Network Interface Cards (NICs)

- Copper: RJ-11 (small, phone jack, landline/DSL), RJ-45 (larger,
    Ethernet)

- Also: Coaxial, Fiber Optic, Wireless

## 2.3 — Legacy Cables

### 2.3.1 — DVI and VGA

⚠ DVI and VGA support only video — not audio. VGA was used for CRT
monitors/projectors (analog).

- DVI-I — supports both analog and digital; DVI-A — analog only;
    DVI-D — digital only

- DVI-D and DVI-I come in single-link and dual-link versions
    (dual-link = extra bandwidth for higher res/refresh)

- The letter tells the signal type: A=Analog, D=Digital, I=Integrated
    (both) — different pin layouts, so types aren't interchangeable

- VGA: 15-pin, D-shell connector with screws; standard analog
    interface for years, now phased out; tops out around Full HD
    (1920x1080)

### 2.3.3 — Serial Cables (RS-232)

Legacy interface, transmits data one bit at a time over a single wire.
Start/stop/parity bits format and verify transmission. Data rates up to
~115 Kbps.

- Commonly used for external dial-up modems (largely replaced by USB),
    but still found on network equipment for device management
    (console/rollover cables)

- RS-232 specifies 25-pin, but PCs typically use the cheaper 9-pin DB9
    connector

- In Windows, called a Communications (COM) port

- Related legacy connector — PS/2: 6-pin mini-DIN for
    mouse/keyboard; Green = mouse, Purple = keyboard

- RS-232 is considered legacy specifically because of SPEED (~115
    Kbps) — not OS compatibility or connector size

### 2.3.4 — Adapter Cables

An adapter cable connects two different cable types, one at each end.

- Active adapters — use circuitry to convert signals between
    different protocols (e.g., digital HDMI to analog VGA)

- Passive adapters — just convert connector shape, same signaling
    standard underneath (e.g., USB-C to USB-A)

- The real test: does the SIGNAL itself need to change (active) or
    just the connector shape (passive)?

## 2.5 — Additional Resources (Video Recaps & New Details)

### 2.5.1 — Cable Types (recap + visual-ID notes)

- Front panel: USB, speaker/headphone jack, power button, power LED +
    activity light, optical drives (increasingly rare)

- Rear panel: PSU connector + PSU fan, case fans, expansion slots
    (keep covered even when unused, for cooling), I/O shield area

- USB is a serial cable with independent transmit/receive wires —
    data can send and receive simultaneously

- Common color convention (not an official standard): USB 2.0 = black,
    USB 3.0 = blue; 3.1 isn't reliably color-coded

- Type C is becoming dominant — used for power and data, NOT keyed
    (either orientation works)

- HDMI: keyed well, physically robust; carries video, audio, AND
    network connections over one cable

- DisplayPort: looks similar to HDMI but has ONE cut edge (HDMI has
    two) — a reliable physical ID tell

- VGA: almost always blue, always 15 pins — don't confuse with the
    9-pin serial RS-232 connector (also sometimes blue); pin count is
    the reliable tell

- SATA data cable can come loose over time/vibration — worth
    checking first during troubleshooting

- Molex: one of the oldest power connectors still around — older
    drives, some fans/RGB lighting today

### 2.5.2 — Motherboards (recap + new framing)

- Analogy: motherboard = nervous system, CPU = brain — every
    component's signal routes through the motherboard to reach the CPU

- Bus = a set of wires letting two components communicate; bus width
    varies (4-bit, 8-bit, 128-bit, etc.) for different jobs

- Named buses: Memory bus (CPU↔RAM), Data bus (storage/other systems),
    Video bus (video card), Front-side bus (chipset-related)

- Proprietary motherboards (e.g., Dell) — designed for a specific
    case, cannot be swapped, replacement must be the exact same model

- Standardized motherboards (ATX, ITX) — fit any compliant case,
    pair with a matching standardized PSU — far more
    repairable/upgradeable

- PCI/PCIe is now the dominant expansion bus standard; slots are
    sometimes color-coded but not reliably — labels and physical
    size/lane count are the reliable ID method

2.6a — SCSI (Small Computer System Interface) — legacy storage

Legacy storage interface, superseded by SATA (consumer) and SAS
(enterprise/servers) — SAS is essentially SCSI's modern serial
successor.

- Devices are daisy-chained on a shared bus (unlike SATA's dedicated
    cable per drive)

- Each device needs a unique ID: Narrow SCSI = IDs 0-7 (8 devices
    max); Wide SCSI = IDs 0-15 (16 devices max)

- Both PHYSICAL ENDS of the SCSI bus chain must be terminated,
    regardless of which device ID sits there — absorbs the signal
    instead of letting it reflect back and corrupt data

- Termination depends on physical position (start/end of chain), not
    device ID — a common exam trap

2.6b — CPU Architecture for Virtualization Hosts

Scenario: choosing the best CPU for a server hosting several hundred
VMs. Answer: x64.

- Hundreds of VMs demand massive memory capacity — x64 breaks past
    32-bit x86's ~4GB addressing ceiling

- x86/x64 platforms carry the hardware virtualization support
    (VT-x/AMD-V) hypervisors depend on

- x86 (32-bit) is RAM-capped in a way that would cripple this host;
    ARM is built for performance-per-watt, not this profile;
    'Emulation' isn't a chip architecture at all

**Quick Self-Check (from module notes)**

- What are the four SATA revisions' speeds in Gbps and MBps?

- What color is the Molex 12V wire vs the 5V wire?

- Name all three motherboard form factors and their exact dimensions

- What's the difference between DVI-A, DVI-D, and DVI-I?

- Which 3.5mm jack color is the microphone input?

- What's the correct order of steps for motherboard installation?

- Why can't you mix SATA and eSATA cables?

- Which motherboard connector types would you check if a case's
    front-panel power button and USB ports stopped responding?

- What is daisy chaining, and which two interfaces from this module
    support it?
