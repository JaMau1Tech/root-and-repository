# Module 2 Practice Questions

*Installing Motherboards and Connectors — CompTIA A+ Core 1 (220-1201)*

No graded lesson-review or quiz data was captured for this module, so all questions below are application-style, built directly from the confirmed content in `module-02-study-notes.md` and `module-02-objectives.md`.

---

## 2.1 — Cables and Connectors

**Q1.** A technician sees a USB-C port on a laptop and assumes it must support at least USB 3.0 speeds. Is this assumption correct?

A. Yes — USB-C only exists on USB 3.0+ devices
B. No — USB-C is a connector shape, not a speed standard; a USB-C port could run anything from USB 2.0 to Thunderbolt underneath
C. Yes — USB-C ports are always color-coded blue to confirm 3.0+ speed
D. No — USB-C only ever runs at USB 2.0 speeds

**Correct: B.**
Why: Stated directly in 2.1.4 — never assume speed from connector shape alone; check documentation.

- **A is wrong** — This is the exact trap the notes warn about: connector shape ≠ speed.
- **C is wrong** — There is explicitly no official color standard for USB ports; blue is a common convention, not a guarantee.
- **D is wrong** — USB-C can run high-speed standards including Thunderbolt; it's not capped at 2.0.

---

**Q2.** What color is the Molex 12V wire, and what color is the 5V wire?

A. 12V = Yellow, 5V = Red
B. 12V = Red, 5V = Yellow
C. 12V = Black, 5V = Red
D. 12V = Yellow, 5V = Black

**Correct: A.**
Why: Fixed, memorizable color code from 2.1.14 — Red = 5VDC, Yellow = 12VDC, Black = Ground.

- **B swaps the two live wires** — a classic exam trap the notes call out directly.
- **C confuses Ground (Black) with a live voltage.**
- **D pairs 12V correctly but mislabels 5V as Ground instead of Red.**

---

**Q3.** A device uses standard eSATA to connect an external 2.5" drive, but the drive doesn't power on. What's the most likely explanation?

A. eSATA cables have a maximum length of only 0.5m
B. Standard eSATA does not supply power over the cable
C. eSATA is incompatible with all 2.5" drives
D. The drive needs a SATA Rev 3 port specifically

**Correct: B.**
Why: Directly stated as a real limitation in 2.1.15/2.2.4 — standard eSATA carries no power; eSATAp (adds USB power) is the variant that does.

- **A is wrong** — eSATA's max length is 2 meters, not 0.5m.
- **C is wrong** — eSATA is a standard external storage interface; it's not incompatible with 2.5" drives, it just lacks power delivery.
- **D is wrong** — SATA revision (1/2/3) governs speed, not power delivery.

---

## 2.2 — Motherboards

**Q4.** Which motherboard form factor supports the most expansion slots, and how many?

A. Mini-ITX — 1 slot
B. Micro-ATX — 4 slots
C. ATX — 7 slots
D. ATX — 4 slots

**Correct: C.**
Why: From the memorized form-factor table in 2.2.7 — ATX (12" x 9.6") supports up to 7 expansion slots, the most of the three.

- **A is a true statement but doesn't answer "the most."**
- **B is a true statement about Micro-ATX but not the maximum.**
- **D incorrectly assigns ATX Micro-ATX's slot count (4) instead of its own (7).**

---

**Q5.** During motherboard installation, a technician installs an extra standoff in a position that doesn't align with any motherboard mounting hole, directly under bare board material. What is the risk?

A. The board will simply not power on until the extra standoff is removed
B. The extra standoff can short-circuit the board
C. This has no effect since standoffs only provide physical support
D. The I/O shield will not seat correctly

**Correct: B.**
Why: Stated directly in 2.2.8 — a standoff under bare board material with no matching hole is a direct short-circuit risk against the board.

- **A is wrong** — the danger isn't a simple boot failure, it's electrical damage.
- **C is wrong** — standoffs are not purely mechanical; misplacement carries real electrical risk exactly because the board's underside carries traces/circuitry.
- **D is wrong** — the I/O shield is a separate installation step (step 2) unrelated to standoff placement.

---

**Q6.** A PCIe x8 card is installed in a physical x16 slot. What happens?

A. The card will not fit at all — this is not possible
B. The card can run at its native x8, though it may fall back lower in some cases (up-plugging)
C. The slot forces the card to run at x16 automatically
D. The motherboard will refuse to POST

**Correct: B.**
Why: Stated directly in 2.2.5 — up-plugging (fewer-lane card in a bigger slot) runs at the card's native lane count, though it may fall back further depending on configuration.

- **A is wrong** — Up-plugging is explicitly supported; a smaller card fits fine in a larger slot.
- **C is wrong** — A card can't exceed its own native lane count just because the slot is bigger — the card is still an x8 device.
- **D is wrong** — Nothing in the notes suggests up-plugging causes a POST failure; it's a normal, supported configuration.

---

**Q7.** A slot on a motherboard is labeled "x16 @ x8." What does this mean?

A. The slot has 16 physical lanes and always runs all 16
B. The slot is physically sized for a x16 card but only wired for 8 lanes of actual bandwidth
C. The slot supports 16 devices simultaneously
D. This label indicates a manufacturing defect

**Correct: B.**
Why: Directly warned about in 2.2.5 — a slot may support fewer lanes than its physical size suggests; always check the motherboard's own label rather than assuming full-size = full-lane-count.

- **A is wrong** — this is the exact assumption the notes warn against.
- **C is wrong** — lane count is about bandwidth to one device, not the number of devices.
- **D is wrong** — this labeling is a normal, intentional motherboard design choice (often due to lane-sharing), not a defect.

---

**Q8.** What is the key physical/functional difference between a 3-pin and a 4-pin case fan connector?

A. 3-pin uses PWM; 4-pin uses voltage control
B. 4-pin uses PWM (via the blue wire) for finer speed control; 3-pin uses cruder voltage-based control
C. There is no functional difference, only connector shape
D. 3-pin fans cannot be used in any modern system

**Correct: B.**
Why: Stated directly in 2.2.10 — 4-pin PWM control is more precise than 3-pin voltage-based control.

- **A reverses the two** — a classic easy mix-up the notes flag.
- **C is wrong** — there is a real functional difference (control method/precision), not just shape.
- **D is wrong** — a 3-pin fan plugged into a 4-pin header still works, just without fine speed variation.

---

## 2.3 — Legacy Cables

**Q9.** What makes RS-232 (serial) a "legacy" interface, specifically?

A. It is not compatible with any modern operating system
B. Its connector is too large for modern cases
C. Its speed (~115 Kbps) is far below modern standards
D. It cannot be used with network equipment

**Correct: C.**
Why: Stated directly and explicitly in 2.3.3 — RS-232 is legacy specifically because of speed, not OS compatibility or connector size (a common exam trap the notes call out by name).

- **A is wrong** — explicitly contradicted; RS-232/serial ports remain OS-supported (Windows calls it a COM port) even today.
- **B is wrong** — connector size isn't the reason; the 9-pin DB9 is actually fairly compact.
- **D is wrong** — RS-232 is explicitly still used today for network equipment console/rollover cables — the opposite of the claim.

---

**Q10.** An adapter converts digital HDMI signal to analog VGA. What type of adapter is this, and why?

A. Passive — because it only changes the connector shape
B. Active — because it uses circuitry to convert the signal itself between genuinely different protocols
C. Passive — because HDMI and VGA carry identical signal types
D. Neither — HDMI cannot be adapted to VGA under any circumstances

**Correct: B.**
Why: Stated directly in 2.3.4 — the real test is whether the *signal itself* needs to change (active) or just the connector shape (passive). Digital-to-analog conversion requires actual signal conversion circuitry.

- **A and C are wrong** — they both misclassify this as passive, but HDMI (digital) and VGA (analog) are fundamentally different signal types, requiring active conversion.
- **D is wrong** — this conversion is explicitly used as the notes' own example of an active adapter.

---

## Additional Resources — SCSI

**Q11.** On a SCSI bus with 5 devices connected in a chain, which device(s) need termination?

A. Only the device with the highest ID number
B. Every device on the chain
C. Only the two devices at the physical ends of the chain, regardless of their ID numbers
D. Only the device with ID 0

**Correct: C.**
Why: Stated directly in the Additional Resources section — termination depends on physical position (start/end of the chain), not device ID. This is explicitly called out as a classic exam trap.

- **A and D are wrong** — they both mistake device ID for the deciding factor; ID number is irrelevant to which devices need termination.
- **B is wrong** — terminating every device (rather than just the two physical ends) is incorrect and not how SCSI bus termination works.

---

## Missed-Concept Watchlist

No real graded quiz data exists yet for this module — nothing to log here.
