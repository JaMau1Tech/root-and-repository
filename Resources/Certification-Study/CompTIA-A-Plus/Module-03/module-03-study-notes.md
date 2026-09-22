# Module 3 Study Notes

*Installing System Devices — Memory & CPU — CompTIA A+ Core 1
(220-1201)*

Memory (RAM)

### 3.3.3 — Memory Modules

Memory modules are printed circuit boards holding a group of RAM chips
acting as a single unit. Desktop memory = DIMM (Dual Inline Memory
Module, chips on both sides); laptops use the smaller SODIMM. Older SIMM
modules had chips on one side only.

- Notches on the edge connector identify DDR generation (DDR3/4/5) and
    prevent wrong-generation insertion (keying)

- DIMMs often have heat sinks due to high clock speeds

- DIMM vs SODIMM: DIMM = desktop/server, higher capacity/performance;
    SODIMM = laptops/compact, lower capacity (4-32GB typical)

- DDR generation must match motherboard slot exactly — no
    cross-generation compatibility

- Mixing speeds is possible but not recommended — system runs at the
    slowest module's speed

- ⚠ ESD-sensitive — always use anti-static precautions when handling

### 3.3.5 — Multi-Channel System Memory

Dual-channel architecture (developed by Intel/AMD) addresses memory as a
system bottleneck. Single-channel = one 64-bit bus; dual-channel = two
64-bit pathways = 128 bits/transfer (2x bandwidth). Requires CPU +
memory controller + motherboard support — ordinary RAM modules are
used, there is no special 'dual-channel' RAM.

- Dual-channel kits sold in stores = just matched identical modules,
    nothing special about the sticks

- Slots typically color-coded in pairs per channel (e.g., Channel A /
    Channel B)

- Matching modules must have same clock speed, capacity, timings, and
    latency — mismatch = system defaults to lowest common value

- Mismatched modules can trigger: single-channel fallback, disabled
    spare module, or Flex Mode (partial dual-channel + partial
    single-channel)

- Triple/quad-channel exists on supported CPUs; unpopulated slots =
    fewer active channels

- DDR5: each module has 2x 32-bit internal channels — 4 total in a
    dual-channel config — improves density and reduces latency

### 3.3.6 — Memory Troubleshooting

Primary RAM troubleshooting method: swap with a known-good stick. RAM
identified by notch position matching the slot's key — a DDR3 stick
physically cannot fit a DDR4 slot.

- If a module won't seat properly: check notch alignment and
    orientation — never force it

- Forcing RAM in risks bending pins and damaging the module or
    motherboard

- Troubleshooting checklist: right generation? notch aligned?
    fully/evenly seated? swap test with known-good stick?

### 3.3.8 — ECC RAM

ECC (Error Correction Code) RAM is used in servers/workstations for
reliability. It detects and corrects single-bit errors automatically;
detects (but cannot correct) multi-bit errors, causing a system halt.

- Adds an 8-bit checksum per transfer → requires 72-bit bus vs
    standard 64-bit

- Memory controller calculates and compares checksums to detect errors

- ECC RAM usually ships as RDIMM (Registered DIMM) — register chip
    reduces controller load, slight performance penalty

- UDIMM = standard consumer format, usually non-ECC (ECC UDIMMs exist
    but are rare)

- CPU AND motherboard must both support ECC for it to function

- Cannot mix UDIMM + RDIMM on the same board; cannot mix ECC + non-ECC
    UDIMMs

- DDR5's internal error-checking ≠ true ECC — DDR5 still has
    separate ECC/non-ECC SKUs

CPUs

### 3.4.1 — CPU Architecture

The CPU executes program instructions via a repeating four-step
instruction cycle:

- Fetch — control unit pulls the next instruction from memory into
    the pipeline

- Decode — control unit interprets the instruction, routes it to ALU
    or FPU

- Execute — ALU (integer) or FPU (floating point) carries out the
    instruction

- Write-back — result is written to a register, cache, or system
    memory

Register = fastest storage, built into CPU, runs at CPU clock speed.
Cache (L1/L2/L3) = near-CPU-speed buffer that reduces trips to slower
system RAM. More/faster cache = fewer memory bottlenecks = better
performance.

### 3.4.2 — x86 CPU Architecture

RISC (Reduced Instruction Set Computing) = small optimized instruction
set, speed/power efficiency, used by ARM (mobile/embedded). CISC
(Complex Instruction Set Computing) = large/complex instruction set,
general-purpose, used by x86 (Intel/AMD, desktop/server).

- x86 = CISC design, supports 32-bit (IA-32) and 64-bit instruction
    sets

- ALU = arithmetic/logic operations; Control Unit = manages
    fetch-decode-execute cycle

- Multi-core = true parallel processing across physical cores

- Hyper-Threading/SMT = one physical core handles multiple threads,
    simulating extra cores

- Cache hierarchy: L1 (smallest/fastest, per-core) → L2 → L3
    (larger/slower, often shared)

### 3.4.3 — x64 CPU Architecture

x86 = original 32-bit instruction set. x64/x86-64 = 64-bit extension —
AMD's version is AMD64, Intel's is Intel 64/EM64T. Unlocks addressing
beyond 4GB RAM.

- 64-bit CPUs can run both 32-bit and 64-bit software; 32-bit CPUs
    CANNOT run 64-bit software

- Drivers must match OS architecture — 64-bit OS requires 64-bit
    drivers

- Windows 11 and modern Linux distros now require 64-bit

- Apple: 64-bit began with the A7 chip (iPhone 5s); macOS Catalina
    dropped 32-bit app support

- x64 enables hardware virtualization: Intel VT-x, AMD AMD-V

- x64 supports DEP (Data Execution Prevention) — blocks code
    execution from non-executable memory regions

### 3.4.4 — ARM CPU Architecture

ARM (Advanced RISC Machines) is a licensed RISC design used by Qualcomm,
Nvidia, Apple, Samsung, etc. — not a single manufacturer's chip.
Found in Apple M1/M2, most Android devices, Chromebooks, some Windows
ARM devices.

- RISC trade-off: more instructions needed per task, but each
    completes in a single clock cycle → better
    performance-per-watt/battery life

- ARM designs are typically System-on-Chip (SoC) —
    video/sound/networking/storage controllers integrated into the CPU
    package

- Software must be specifically compiled for ARM — no native x86/x64
    compatibility

- Emulation (Windows on ARM, Apple Rosetta 2) lets x86/x64 software
    run on ARM, with a performance penalty

- ARM SoCs are typically soldered directly to the motherboard —
    smaller, thinner, non-upgradeable

- Low power + efficient heat management → passive cooling (no fan)
    often possible

### 3.4.5 — CPU Features

Clock speed is only a fair comparison within the same architecture.
Performance is capped by thermal/power limits.

- SMT (Intel: Hyper-Threading) = 1 physical core handles multiple
    threads → acts like 2 virtual cores

- SMP (Symmetric Multiprocessing) = multiple physical CPUs, OS
    distributes tasks; CPUs must be identical + SMP-capable

- CMP/multicore = multiple cores on one chip; each core has its own
    execution unit + cache, plus shared cache

- nC/nT notation: e.g. 8C/16T = 8 cores, 16 threads (cores × SMT)

- Virtualization support: Intel VT-x / AMD-V (hardware-assisted
    virtualization)

- SLAT = general term for 2nd-gen virtualization memory translation;
    Intel = EPT, AMD = RVI

- Heavy VM workloads also want: high core count, SMT, and IOMMU
    support

### 3.4.6 — CPU Socket Types

CPU packaging = the physical connection method between CPU and
motherboard. Intel and AMD sockets are never cross-compatible. All
modern sockets use ZIF (Zero Insertion Force) to reduce pin damage risk
during install.

- Intel = LGA (Land Grid Array) — pins on the motherboard, flat pads
    on the CPU. LGA 1200 = 10th/11th gen Core; LGA 1700 = 12th gen
    (Alder Lake)

- AMD = traditionally PGA (Pin Grid Array) — pins on the CPU. AM4 =
    Ryzen (PGA). TR4 = Threadripper (LGA). SP3 = EPYC servers (LGA)

- Install: align Pin 1 to Pin 1. Removal: twist heat sink gently,
    don't pull straight; release latch first

- Reapplying thermal paste: clean old paste, apply new sparingly
    (small X pattern) — excess can damage the socket

- ⚠ CPUs are ESD-sensitive — anti-static precautions required

### 3.4.7 — CPU Types and Motherboard Compatibility

Compatibility requires matching BOTH the physical socket AND the chipset
— a CPU can physically fit and still not work if the chipset/BIOS
doesn't support that model.

- Chipset determines available features: overclocking, PCIe lanes,
    memory support (Intel Z-series/AMD X-series = high-end)

- Form factor: ATX \> microATX \> Mini-ITX (more slots/RAM capacity as
    size increases)

- Install order: align socket → seat CPU → pea-sized thermal paste
    (center) → attach cooler → mount board

- Single-core = 1 task; multi-core = simultaneous tasks; SMT = 2
    threads/core

- Gaming favors high single-core performance;
    virtualization/workstation favors core count + multithreading

- Desktop: Intel Core i3-i9 (+Pentium/Celeron budget); AMD Ryzen 3-9
    (+Threadripper)

- Desktop sockets: Intel LGA 1700 (current); AMD AM4 (PGA) → AM5 (LGA,
    DDR5/PCIe 5.0)

- Server: multisocket boards, large ECC RAM, expanded cache. Xeon
    sockets: LGA 4189 (current), LGA 3647 (older). EPYC sockets: SP3,
    SP5 (newer)

- Mobile CPUs: ARM common for efficiency; often soldered =
    non-upgradeable

### 3.4.8 — Install a Processor

CPU install is typically one of the last build steps. Align the gold
arrow (CPU) to the white dot/arrow (socket), plus any additional
notches. Never force the CPU in — forcing risks bent pins and a ruined
processor.

- Seat CPU → lower cage → lower lever → lock

- Thermal paste: small blob, center of CPU, before heat sink goes on

- Heat sink install varies by brand (Intel vs AMD) — check
    specifics; push down + twist levers to lock, ensure firm even seal

- Final step: plug CPU fan into the motherboard's CPU fan header —
    no cooling works without this

System Memory & Component Matching

### 3.6.1 — System Memory

RAM = volatile memory (loses data on power-off); ROM = non-volatile
(retains data). SIMM (old, one-sided) → DIMM (modern, chips both sides)
→ SODIMM (laptop-size).

- Cache = tiny memory inside the CPU, runs at CPU clock speed,
    momentary storage only

- System RAM holds active app data plus OS kernel/services — not
    just user files

- RAM full → CPU forced to use the hard drive (much slower) — this
    fallback space is virtual memory / swap file / page file (all the
    same concept)

- CPU↔RAM connection = front side bus (FSB), via the north bridge

- No RAM installed → system won't boot, continuous POST beep code

- 32-bit → 4GB max virtual memory; 64-bit (40-bit address bus) → up to
    256TB

- RAM = random access (any address, any order); FIFO devices = strict
    in-order only

- Buy RAM by capacity (GB) + speed — must match motherboard support;
    key/notch alignment is mandatory

- Motherboard auto-detects installed RAM — no manual configuration
    required

### 3.6.2 — Matching Computer Components

'The Big Three' = Motherboard + CPU + RAM — all must be compatible
together. Builds are usually anchored around the motherboard or the CPU.

- Motherboard specs to check: socket type, supported CPU series,
    chipset, memory type, supported speeds, max capacity, channel
    support, buffered/unbuffered RAM support

- CPU: socket + series must match the motherboard exactly; core
    count/clock speed = personal choice within that constraint

- RAM: type + speed + pin count must match the motherboard;
    capacity/dual-channel kit = personal choice within that constraint

- Dual-channel kits = matched module pairs sold together (e.g., 32GB
    kit = 2×16GB)

- Buffered RAM = mostly server-grade, often unsupported on consumer
    boards

- Matching checklist: socket↔socket, series↔series, memory
    type/pins↔memory type/pins, speed↔speed — everything else is
    optional/preference
