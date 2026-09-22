# Module 3 Objectives — In-Depth

*Installing System Devices — CompTIA A+ Core 1 (220-1201)*

## 3.3 — Compare and contrast RAM characteristics

Memory modules are printed circuit boards holding a group of RAM chips
acting as a single unit. Desktop systems use the standard-size DIMM
(Dual Inline Memory Module, with chips on both sides), while laptops use
the smaller SODIMM; older SIMM modules had chips on one side only. A
notch on the module's edge connector identifies its DDR generation and
physically prevents inserting the wrong generation into a slot. DIMMs
often carry heat sinks due to their high clock speeds, and handling any
RAM module requires anti-static precautions, since RAM is ESD-sensitive.

A major performance feature is dual-channel architecture, developed by
Intel and AMD to address memory as a system bottleneck. Single-channel
memory uses one 64-bit data bus between CPU, controller, and RAM;
dual-channel uses two 64-bit pathways for 128 bits per transfer,
doubling bandwidth. This requires support from the CPU, memory
controller, and motherboard — the RAM modules themselves are entirely
ordinary; there's no such thing as special 'dual-channel' RAM, only
matched identical modules sold together as a kit. Motherboard slots are
typically color-coded in pairs per channel. For dual-channel to actually
engage, paired modules must match in clock speed, capacity, timings, and
latency — a mismatch causes the system to default to the lowest common
value across whatever's installed. Populating channels unevenly can
trigger a single-channel fallback, a disabled spare module, or 'Flex
Mode,' where the overlapping capacity runs dual-channel and the
remainder runs single-channel. DDR5 takes this further by giving each
module two internal 32-bit channels, which in a dual-channel
configuration yields four total channels, improving density and reducing
latency.

When troubleshooting RAM, the primary method is swapping in a known-good
stick. Because the notch position is generation-specific, a DDR3 module
simply cannot physically fit a DDR4 slot. If a module won't seat
properly, check notch alignment and orientation rather than forcing it
— forcing risks bending pins and damaging the module or motherboard
permanently. A practical troubleshooting checklist: confirm the correct
generation, confirm notch alignment, confirm even full seating on both
sides, then run a known-good swap test if the problem persists.

For environments where reliability outweighs raw performance — servers
and workstations — ECC (Error Correction Code) RAM adds an 8-bit
checksum to every data transfer, requiring a 72-bit bus instead of the
standard 64-bit. The memory controller calculates and compares this
checksum to detect errors: single-bit errors are corrected automatically
and transparently, while multi-bit errors are detected but cannot be
corrected, forcing a system halt rather than risking silent data
corruption. Most ECC RAM ships as RDIMM (Registered DIMM), which
includes a register chip that reduces electrical load on the memory
controller at a slight performance cost; standard consumer RAM is UDIMM
(Unbuffered DIMM), which is usually non-ECC, though ECC UDIMMs do exist.
For ECC to function, both the CPU and motherboard must support it, and
you cannot mix UDIMM with RDIMM on the same board, nor mix ECC with
non-ECC UDIMMs. DDR5's built-in internal error-checking is a different
mechanism entirely from true ECC — DDR5 still ships in separate ECC
and non-ECC variants.

At a systems level, RAM is volatile memory: everything stored in it is
lost the instant power is cut, in contrast to non-volatile ROM. RAM's
job is to hold actively-used data — both running applications and the
OS kernel/services — that the CPU reads from far faster than it could
read from storage. A small amount of even faster memory, cache
(L1/L2/L3), sits inside or very close to the CPU itself and runs at or
near the CPU's own clock speed, holding the most frequently accessed
data to reduce trips out to slower system RAM. When RAM fills up, the
CPU is forced to fall back on virtual memory — also called the swap
file or page file — space borrowed from the much slower hard drive.
Address space for this virtual memory has grown dramatically: 32-bit
systems were capped around 4GB, while 64-bit systems with a 40-bit
address bus can theoretically address up to 256TB. Physically, RAM is
buy-to-spec: capacity in gigabytes and speed must both match what the
motherboard supports, and the module's key/notch must align correctly
during installation, or you risk damaging both the RAM and the board.
Once correctly seated, the motherboard automatically detects installed
capacity with no manual configuration required.

## 3.4 — Compare and contrast storage devices

This module traces the historical progression of storage technology.
Floppy disks (introduced 1971) offered barely a megabyte of magnetic
storage and were fragile and slow. CDs and DVDs introduced optical
storage, using a laser to read data, dramatically increasing capacity
into the hundreds of megabytes and multiple gigabytes respectively, and
enabling cheap mass distribution of software and video. USB flash drives
and SSDs then eliminated moving parts entirely, dramatically improving
speed, durability, and portability while pushing capacity into the
terabyte range. The most significant recent shift is cloud storage,
which removes the physical medium from the equation entirely — data
lives on remote servers accessed over the internet from any connected
device, trading a fragile, single-location, low-capacity model for a
durable, high-capacity, instantly accessible one, at the cost of new
tradeoffs around security and dependence on connectivity. Across this
entire progression, each generation solved the prior generation's
biggest limitation (capacity, speed, durability, or portability) while
introducing a new tradeoff of its own — moving data further from
fragile moving parts and closer to instant, always-available access.

## 3.5 — Given a scenario, install and configure motherboards, CPUs, and
add-on cards

Every CPU processes instructions through a repeating four-step cycle:
fetch (the control unit pulls the next instruction from memory into the
pipeline), decode (the control unit interprets it and routes it to the
ALU for integer math or the FPU for floating-point math), execute (the
ALU or FPU actually carries out the operation), and write-back (the
result is written to a register, cache, or system memory). Registers are
the fastest storage in the entire system — tiny, built directly into
the CPU, running at the CPU's own clock speed — while cache (L1
smallest/fastest and closest to each core, up through L2 and the larger,
slower, often-shared L3) buffers frequently used data to reduce how
often the CPU has to reach out to comparatively slow system RAM. More
and faster cache directly translates to fewer memory bottlenecks and
better real-world performance.

Two competing instruction-set philosophies define modern CPU
architecture. RISC (Reduced Instruction Set Computing) uses a small,
optimized instruction set that trades needing more instructions per task
for each instruction completing in a single clock cycle, yielding
excellent performance-per-watt — this is the ARM architecture used
throughout mobile and embedded devices. CISC (Complex Instruction Set
Computing) uses a larger, richer instruction set that can accomplish
more per instruction at higher power cost — this is the x86
architecture from Intel and AMD used in desktops and servers. x86 itself
refers to the original 32-bit instruction set; x64 (also called x86-64)
is the 64-bit extension developed by AMD as AMD64 and adopted by Intel
as Intel 64/EM64T, unlocking memory addressing far beyond 32-bit's
roughly 4GB ceiling. A 64-bit CPU can run both 32-bit and 64-bit
software, but a 32-bit CPU can never run 64-bit software, and device
drivers must always match the OS's bit architecture. x64 also enables
hardware-assisted virtualization (Intel VT-x, AMD AMD-V) and DEP (Data
Execution Prevention), a security feature blocking code execution from
memory regions marked non-executable.

ARM itself is a licensed RISC design, not a single company's product
— Qualcomm, Nvidia, Apple, and Samsung all produce their own ARM-based
chips, found in Apple's M-series, most Android devices, Chromebooks,
and some Windows ARM laptops. ARM designs are typically built as a
System-on-Chip (SoC), integrating video, sound, networking, and storage
controllers directly into the CPU package, which is a major reason ARM
suits compact, fanless, battery-powered devices. Software must be
specifically compiled for the ARM instruction set — there's no native
x86/x64 compatibility — so running existing x86/x64 software on ARM
requires emulation (Windows on ARM, Apple's Rosetta 2), which
introduces a real performance penalty in exchange for compatibility. ARM
SoCs are typically soldered directly to the motherboard rather than
socketed, trading upgradeability for a smaller, thinner, more durable
design, and their low power draw often allows passive cooling with no
fan at all.

Beyond raw architecture, several features boost real-world CPU
performance. SMT (Simultaneous Multithreading, branded Hyper-Threading
by Intel) lets a single physical core process multiple threads
concurrently, effectively acting like two virtual cores and reducing
idle execution time. SMP (Symmetric Multiprocessing) uses two or more
entire physical CPUs in one system, with an SMP-aware OS distributing
tasks across them regardless of whether individual applications are
multithreaded — this requires identical, SMP-capable CPUs in every
socket, and is mostly found in servers and high-end workstations due to
the cost of multi-socket boards. CMP, or simply multicore, places
multiple processing cores on a single chip, delivering multi-processing
benefits without SMP's socket-count expense; each core has its own
execution unit and cache, often alongside a larger shared cache. The
nC/nT notation captures both core count and thread count together — an
8C/16T CPU has 8 physical cores and, through SMT, can process 16 threads
simultaneously. For virtualization workloads specifically,
hardware-assisted virtualization (Intel VT-x, AMD-V) is essential, along
with second-generation virtualization features for efficient memory
translation between VMs and physical hardware — SLAT is the general
term, with Intel's implementation called EPT and AMD's called RVI —
plus high core counts, SMT, and IOMMU support for managing how VMs
access physical I/O devices.

Physically installing a CPU requires matching the correct socket type,
since Intel and AMD sockets are never cross-compatible, and even
different generations within the same brand can use different sockets.
All modern sockets use a ZIF (Zero Insertion Force) mechanism, letting
the CPU be seated without pressure to minimize pin-damage risk. Intel
predominantly uses LGA (Land Grid Array), where pins live on the
motherboard socket and the CPU has flat contact pads — common sockets
include LGA 1200 (10th/11th gen Core) and LGA 1700 (12th gen Alder Lake
and newer). AMD traditionally uses PGA (Pin Grid Array), where pins live
on the CPU itself — AM4 for Ryzen uses PGA — though AMD's
higher-end lines have moved to LGA: TR4 for Threadripper and SP3 for
EPYC servers both use LGA. During installation, align Pin 1 on the CPU
to Pin 1 on the socket (often marked with a small gold arrow on the chip
matched to a white dot or arrow on the socket), never force the CPU in,
and apply thermal paste as a small blob in the center of the processor
before attaching the heat sink, using a firm, even, twisting motion to
lock the heat sink levers for full contact. The very last step — easy
to forget, but critical — is connecting the CPU fan cable to the
motherboard's CPU fan header, since nothing else in the process
provides active cooling without it.

Compatibility between CPU and motherboard requires matching both the
physical socket AND the chipset simultaneously — a CPU can physically
fit a socket and still fail to work if the chipset or firmware doesn't
explicitly support that specific model. The chipset also determines
available features like overclocking support, PCIe lane count, and
memory support, with higher-end chipsets (Intel's Z-series, AMD's
X-series) unlocking more of these features than budget chipsets.
Building or upgrading a system, therefore, always requires matching what
the course calls 'the Big Three' — motherboard, CPU, and RAM —
checking that CPU socket and series match the motherboard exactly, and
that RAM type, speed, and pin count also match what the motherboard
supports; everything beyond that (core count, RAM capacity, heat sink
choice) is personal preference within those hard constraints.

## 3.6 — Given a scenario, install or replace the appropriate power
supply

A PSU's core job is converting AC input voltage from the wall into the
DC voltages the motherboard and every internal component actually need
to run. Voltage is the electrical force pushing current through a
circuit, current is the actual flow of electric charge, and wattage —
the product of voltage and current together — is the real-world figure
that determines how much total power a PSU can deliver across all its
rails simultaneously; this is why a PSU is sized and shopped for by its
wattage rating rather than by voltage or current in isolation.

Heat is an unavoidable byproduct of every component drawing current,
since electrical resistance in the CPU, GPU, and other chips converts
some of that energy into thermal output instead of useful work. Left
unmanaged, this heat degrades performance and can permanently damage
hardware, which is why cooling systems exist specifically to move heat
away faster than it accumulates: a heat sink draws heat off the chip
through direct physical contact, a fan then pushes air across the heat
sink's fins to carry that heat away from the component, and liquid
cooling — using a coolant loop between a CPU block and an external
radiator — moves substantially more heat than air cooling alone,
making it the choice for particularly high-load systems.

Learning Outcomes (from Lesson 3.4 — CPUs)

**What are the four basic operations performed by the CPU on each
instruction, and how can understanding these operations help in
optimizing server performance?**

Fetch, decode, execute, and write-back. The control unit fetches the
next instruction from memory, decodes what it means and routes it to the
ALU or FPU, the ALU/FPU executes it, and the result is written back to a
register, cache, or memory. Understanding this cycle matters for
performance tuning because bottlenecks show up at specific stages — a
slow fetch stage often points to memory or bus speed limits, while cache
size and speed directly affect how often the CPU stalls waiting on
comparatively slow system RAM. This is exactly why server CPUs are built
with large L2/L3 caches: more cache means fewer round-trips to slow
memory and better real-world throughput.

**What are the key differences between ARM's RISC architecture and the
CISC architecture used in x86/x64 CPUs, and how do these differences
impact performance and power efficiency?**

RISC (ARM) uses a small, optimized instruction set where each
instruction completes in a single clock cycle, trading more total
instructions per task for excellent performance-per-watt — ideal for
mobile and embedded devices. CISC (x86/x64) uses a larger, more complex
instruction set that can accomplish more per instruction at higher power
cost, suited to the general-purpose, plugged-in workloads of desktops
and servers.

**What is Simultaneous Multithreading (SMT), and how does it enhance
performance in multithreaded applications?**

SMT (branded Hyper-Threading by Intel) allows a single physical core to
process multiple threads concurrently by interleaving them, so the
core's execution units stay busier and idle time drops. This boosts
throughput specifically on software built to use multiple threads —
video editing, gaming, running virtual machines — by letting one core
act like two virtual cores.

**What is the difference between Intel's Land Grid Array (LGA) and
AMD's Pin Grid Array (PGA) socket types, and why is it important to
match the CPU and motherboard socket types?**

LGA puts the pins on the motherboard socket itself, with the CPU
carrying flat contact pads (Intel's traditional approach). PGA puts the
pins on the CPU itself, which insert into the motherboard socket (AMD's
traditional approach, e.g., AM4, though AMD's higher-end TR4 and SP3
sockets use LGA instead). Matching socket type matters because it's a
physically different mechanical interface — there is zero
cross-compatibility between LGA and PGA, or between Intel and AMD at
all, regardless of any other spec matching up.

**What are the differences between Intel's Core i3/i5/i7/i9 processors
and AMD's Ryzen 3/5/7/9 processors, and how do these differences impact
the choice of desktop computers for office use?**

Both lineups scale from entry-level to enthusiast/professional tiers (i3
through i9; Ryzen 3 through Ryzen 9), with Intel also offering budget
Pentium/Celeron chips and AMD offering the workstation-grade
Threadripper above Ryzen 9. For office use specifically, single-core
performance and reliability matter more than raw core count or
multithreading, so a mid-tier chip (i5 or Ryzen 5) is typically
sufficient — the higher tiers exist for workloads like gaming, video
editing, or virtualization that actually benefit from the extra cores
and threads.

**What are the key features of server-class CPUs like Intel Xeon and AMD
EPYC, and why are these features important for data center operations?**

Xeon and EPYC are built for scalability and reliability rather than peak
single-core speed: high core counts, support for large amounts of ECC
RAM, expanded cache, and multi-socket motherboard support (multiple
physical CPU packages in one system). These features matter in a
datacenter because server workloads prioritize sustained throughput,
data integrity (ECC's error correction), and the ability to scale by
adding sockets or memory rather than simply running one task as fast as
possible.
