# Module 3 Practice Questions

*Installing System Devices — Memory & CPU — CompTIA A+ Core 1 (220-1201)*

No graded lesson-review or quiz data was captured for this module, so all questions below are application-style, built directly from the confirmed content in `module-03-study-notes.md`.

---

## 3.3 — Memory

**Q1.** A technician installs two RAM modules with different clock speeds into a dual-channel motherboard. What happens?

A. The system won't boot at all
B. The system runs both modules at the slower module's speed
C. The system runs both modules at the faster module's speed
D. Only the faster module is used; the slower one is ignored

**Correct: B.**
Why: Stated directly in 3.3.3 and 3.3.5 — mixing speeds is possible but not recommended, and the system runs at the slowest module's speed. Mismatched dual-channel modules can also trigger single-channel fallback or Flex Mode, but speed itself always defaults to the lowest common value.

- **A is wrong** — mismatched RAM speed doesn't prevent booting, it just limits performance.
- **C is wrong** — this is the opposite of how the system actually resolves the mismatch.
- **D is wrong** — both modules are used; they just run at the reduced common speed rather than one being ignored.

---

**Q2.** A server needs to both correct single-bit memory errors automatically and detect (but not correct) multi-bit errors. Which requirement must be true for this to work?

A. Only the RAM itself needs to support ECC
B. Only the motherboard needs to support ECC
C. Both the CPU and motherboard must support ECC
D. Any standard UDIMM will support this automatically

**Correct: C.**
Why: Stated directly in 3.3.8 — CPU AND motherboard must both support ECC for it to function; ECC RAM alone isn't sufficient.

- **A and B are wrong** — each names only one required component; both must support it together.
- **D is wrong** — standard UDIMMs are usually non-ECC; ECC UDIMMs exist but are described as rare, and "any standard UDIMM" is not a safe assumption.

---

**Q3.** A DDR4 module won't fit into a DDR3 slot no matter how it's oriented. What is the correct troubleshooting conclusion?

A. The slot is damaged and needs replacement
B. This is expected — DDR generations have different notch positions and are not physically cross-compatible; do not force it
C. The module needs to be forced in with firm, even pressure
D. This indicates a bent-pin issue with the motherboard

**Correct: B.**
Why: Stated directly in 3.3.3/3.3.6 — DDR3/4/5 notches physically prevent wrong-generation insertion by design; forcing it risks bending pins and damaging the module or motherboard.

- **A is wrong** — this is expected, correct-by-design behavior, not a defect.
- **C is wrong** — explicitly warned against; never force RAM in.
- **D is wrong** — the notch mismatch is the explanation on its own; no pin damage has occurred yet (forcing it would cause that).

---

## 3.4 — CPUs

**Q4.** Which architecture uses a small, optimized instruction set for speed/power efficiency, and which platform is it associated with?

A. CISC — used by ARM
B. RISC — used by ARM
C. RISC — used by x86
D. CISC — used by x86 and ARM equally

**Correct: B.**
Why: Stated directly in 3.4.2 — RISC = small optimized instruction set for speed/power efficiency, used by ARM (mobile/embedded). CISC = large/complex instruction set, used by x86.

- **A and D are wrong** — they misattribute RISC's traits/association to CISC.
- **C is wrong** — x86 is explicitly the CISC example in the notes, not RISC.

---

**Q5.** A server will host several hundred virtual machines and needs to address well beyond 4GB of memory. Which CPU architecture is required?

A. x86 (32-bit)
B. x64
C. ARM
D. Emulation-based architecture

**Correct: B.**
Why: Stated directly in 3.4.3 — x64 unlocks addressing beyond 4GB RAM, which 32-bit x86 cannot. x64 also carries the hardware virtualization support (VT-x/AMD-V) that hypervisors depend on.

- **A is wrong** — 32-bit x86 is capped around a 4GB addressing ceiling, explicitly cited as inadequate for this scenario.
- **C is wrong** — ARM is optimized for performance-per-watt (mobile/embedded), not this memory-capacity profile.
- **D is wrong** — "Emulation" is not a CPU architecture at all — it's a software technique for running incompatible code, called out directly as a wrong-answer trap in the notes.

---

**Q6.** What is the tradeoff of ARM's RISC design compared to x86's CISC design?

A. ARM requires more instructions per task, but each completes in a single clock cycle, improving performance-per-watt
B. ARM requires fewer instructions per task and uses more power than x86
C. ARM and x86 have identical instruction efficiency; the only difference is licensing
D. ARM cannot run software compiled specifically for it

**Correct: A.**
Why: Stated directly in 3.4.4 — RISC's tradeoff is more instructions needed per task, but each completes in a single clock cycle, which is why ARM achieves better battery life/performance-per-watt.

- **B is wrong** — reverses both halves of the actual tradeoff.
- **C is wrong** — the notes explicitly describe a real efficiency-related design tradeoff, not just a licensing difference.
- **D is wrong** — ARM absolutely runs software compiled for it; it's *x86/x64* software that needs emulation (Rosetta 2, Windows on ARM) to run on ARM.

---

**Q7.** Intel uses LGA sockets; AMD's Ryzen desktop CPUs traditionally use which socket type?

A. LGA, same as Intel
B. PGA (AM4)
C. BGA, soldered directly to the board
D. ZIF is AMD-exclusive; Intel doesn't use it

**Correct: B.**
Why: Stated directly in 3.4.6 — Intel = LGA (pins on the motherboard), AMD = traditionally PGA (pins on the CPU), with AM4 (Ryzen) as the specific named example.

- **A is wrong** — Intel and AMD sockets are explicitly never cross-compatible, and AMD's traditional consumer socket is PGA, not LGA (though the notes do mention some AMD server/HEDT sockets like TR4/SP3 are LGA — AM4 specifically is PGA).
- **C is wrong** — soldered BGA-style packaging isn't how AM4 desktop Ryzen CPUs are described; that's more associated with mobile/embedded ARM SoCs (3.4.4).
- **D is wrong** — ZIF (Zero Insertion Force) is described as used by all modern sockets, not AMD-exclusive.

---

**Q8.** During CPU installation, a technician feels significant resistance while seating the CPU into its socket. What should they do?

A. Apply firm, even pressure to fully seat it
B. Stop and recheck alignment — CPUs should seat with minimal to no force
C. Apply thermal paste first to help it slide into place
D. Attach the heat sink immediately to force proper seating

**Correct: B.**
Why: Stated directly in 3.4.8 — real pressure needed means something's misaligned; stop and recheck rather than force it. Seating should also be verified BEFORE attaching the heat sink.

- **A is wrong** — this is explicitly the RAM-seating guidance (3.4.1 notes RAM needs firm even pressure), not CPU seating — mixing these up is a real point of confusion the notes distinguish carefully.
- **C is wrong** — thermal paste doesn't affect seating and is applied after the CPU is already correctly seated.
- **D is wrong** — the heat sink should only go on after seating is verified, not used to force a seating problem.

---

## 3.6 — Component Matching

**Q9.** When selecting "The Big Three" (motherboard, CPU, RAM) for a build, which specs are true "must-match" requirements rather than personal preference?

A. Core count, RAM capacity, and dual-channel kit choice
B. Socket↔socket, CPU series↔motherboard series, and memory type/pins↔memory type/pins
C. Case color, cooler brand, and power supply wattage
D. Clock speed and capacity only

**Correct: B.**
Why: Stated directly in 3.6.2's matching checklist — socket, series, and memory type/pin compatibility are the mandatory matches; everything else (core count, capacity, dual-channel kit) is explicitly called out as personal choice within that constraint.

- **A and D are wrong** — core count, RAM capacity, clock speed, and dual-channel kit choice are explicitly listed as *optional/preference* items, not mandatory matches.
- **C is wrong** — case color, cooler brand, and PSU wattage aren't part of the Big Three compatibility discussion at all.

---

## Missed-Concept Watchlist

No real graded quiz data exists yet for this module — nothing to log here.
