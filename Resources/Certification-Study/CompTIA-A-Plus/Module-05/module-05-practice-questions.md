# Module 5 Practice Questions

*Comparing Local Networking Hardware — CompTIA A+ Core 1 (220-1201)*

Every lesson review and the Module Quiz in this module were scored 100% on the source notes — no misses to draw from. Questions below are built from the confirmed Key Takeaways content anyway, since a clean score doesn't mean the material doesn't need active-recall reinforcement later.

---

## 5.1 — Network Types

**Q1.** A company has offices in three locations across the same city and wants to connect them without relying purely on Bluetooth or unmanaged wireless. What network type best fits?

A. PAN
B. MAN
C. SOHO
D. Enterprise/private WAN using leased ISP equipment only

**Correct: B — MAN.**
Why: Stated directly in the Key Takeaways — MAN is the best fit for a multi-location company within one city; bigger than a LAN, smaller than a full WAN.

- **A is wrong** — PAN is a few-meter wireless range (wearables/peripherals), nowhere near city-scale.
- **C is wrong** — SOHO describes a small single-site network, not a multi-site city-spanning one.
- **D is wrong** — while enterprise/private WANs do use leased ISP equipment (not Bluetooth/wireless-only, per the same takeaway), a WAN is the broader category for connecting sites across any distance — MAN is the more precise fit for "same city."

---

**Q2.** What is the key functional difference between a router and a switch?

A. A router connects devices within a network; a switch forwards between networks
B. A router forwards BETWEEN networks; a switch connects devices WITHIN a network
C. They perform the same function at different speeds
D. A switch requires an IP address to function; a router does not

**Correct: B.**
Why: Stated directly in the Key Takeaways.

- **A reverses the definitions.**
- **C is wrong** — these are functionally distinct devices operating at different levels (switch = Layer 2/MAC-based within a network; router = Layer 3/IP-based between networks), not merely different speeds of the same function.
- **D is wrong** — reverses reality: switches operate on MAC addresses without needing an IP; routers are the devices that require IP addressing to forward between networks.

---

## 5.2 — Networking Hardware

**Q3.** A switch receives a frame addressed to a MAC address not yet in its MAC address table. What does the switch do?

A. Drops the frame
B. Floods the frame out all ports except the source port
C. Sends the frame only back out the source port
D. Queues the frame until the destination MAC is learned

**Correct: B.**
Why: Stated directly in 5.2.6/5.2.7 — an unknown destination MAC causes the switch to flood the frame out all ports (except the source), since it doesn't yet know which port leads to that address.

- **A is wrong** — the switch doesn't discard unknown-destination frames; it floods them so they still reach their target.
- **C is wrong** — sending only back out the source port would send the frame back where it came from, never reaching the actual destination.
- **D is wrong** — switches don't queue and wait; they flood immediately to avoid delay.

---

**Q4.** A network uses a switch that doesn't natively support PoE, but an AP on that segment needs powered Ethernet. What solves this without replacing the switch?

A. A PoE injector (midspan)
B. Upgrading to 802.3bt automatically fixes this
C. This cannot be solved without replacing the switch
D. Using a longer Ethernet cable

**Correct: A.**
Why: Stated directly in the Key Takeaways — a PoE injector (midspan) enables PoE when the switch itself doesn't support it.

- **B is wrong** — the PoE standard/tier doesn't matter if the switch has no PoE support at all; the injector is what adds the capability regardless of tier.
- **C is wrong** — this is exactly the scenario a PoE injector solves without a switch replacement.
- **D is wrong** — cable length is unrelated to whether a switch can supply power over the line.

---

**Q5.** How do switches and bridges build their MAC address tables?

A. By learning from both source AND destination MAC addresses
B. By learning from SOURCE MAC only — never destination
C. Through manual configuration only
D. By querying a central DNS server

**Correct: B.**
Why: Stated directly in the Key Takeaways as an explicit point.

- **A is wrong** — this overstates it; only the source MAC (where traffic is coming from) builds the table, not the destination.
- **C is wrong** — the table is built dynamically from observed traffic, not manual configuration (that's what makes unmanaged switches plug-and-play).
- **D is wrong** — MAC learning is a Layer 2 switch function entirely separate from DNS, which resolves names to IP addresses at a different layer.

---

## 5.3 — Network Cable Types

**Q6.** A cable exhibits crosstalk. What is the cause, and where is it strongest?

A. Interference from an external fluorescent light; strongest at the far end
B. Interference between two pairs within the same cable, caused by excessive untwisting during termination, strongest at the "near end"
C. A break in the outer jacket; strongest in the middle of the run
D. Signal loss due to distance exceeding 100m

**Correct: B.**
Why: Stated directly in the Key Takeaways.

- **A is wrong** — crosstalk is internal (between pairs in the same cable), not caused by an external light source — that would be a different interference type (which is what STP/shielding protects against).
- **C is wrong** — crosstalk isn't about jacket damage or a middle-of-run break.
- **D is wrong** — that describes attenuation over distance, a separate issue from crosstalk.

---

**Q7.** A cable run needs to be Cat 6A, run through a drop ceiling used as an HVAC return air path, and support Gigabit speeds at the full 100m. Which requirement is easiest to overlook?

A. The Gigabit speed requirement
B. The Cat 6A requirement
C. The plenum-rated cable requirement, since the cable is passing through an HVAC void
D. None — all single-constraint questions are equally easy

**Correct: C.**
Why: Stated directly in the Key Takeaways — combined-constraint questions (plenum + Gigabit + twisted-pair, in this exact combination) require checking every stated requirement, not just the first match; the plenum/fire-code requirement is the one most likely to get missed when focus goes to the cable category and speed.

- **A and B are wrong** — these are the "obvious" requirements that are easy to spot; the takeaway specifically warns about the requirement that's easy to *miss*, which is the plenum rating.
- **D is wrong** — this question is explicitly a multi-constraint scenario, not a single-constraint one, which is exactly the pattern the takeaway warns about.

---

**Q8.** What is pin 1 on a T568A-terminated RJ45 connector?

A. Orange
B. Orange with white stripe
C. Green with white stripe
D. Solid green

**Correct: C.**
Why: Stated directly in the Key Takeaways — T568A pin 1 = green with white.

- **A and D are wrong** — solid orange and solid green are not pin 1 under T568A (per 5.3.5, pin 2 = solid green under T568A).
- **B is wrong** — orange/white is T568A's pin 3, not pin 1 (T568A and T568B swap the orange and green pair positions, which is the classic point of confusion here).

---

## 5.4 — Wireless Networking

**Q9.** What causes 802.11a to be incompatible with 802.11b/g?

A. 802.11a uses a proprietary encryption method
B. 802.11a operates at 5.75 GHz, a different band than 802.11b/g's 2.4GHz
C. 802.11a has a shorter maximum range
D. 802.11a requires a wired connection

**Correct: B.**
Why: Stated directly in the Key Takeaways — the band difference (5.75 GHz vs 2.4GHz) is explicitly named as *why* 802.11a is incompatible with 802.11b/g, not encryption or range.

- **A is wrong** — encryption method isn't the stated cause of this specific incompatibility.
- **C is wrong** — range is a real difference between the standards but isn't cited as the cause of incompatibility; the band is.
- **D is wrong** — 802.11a is a wireless standard; this doesn't apply.

---

**Q10.** A business needs a long-range wireless link with guaranteed freedom from third-party interference and legal recourse if interference occurs. What spectrum choice fits?

A. Unlicensed 2.4GHz
B. Unlicensed 5GHz
C. Licensed spectrum
D. Any spectrum, since range is the only real variable

**Correct: C.**
Why: Stated directly in the Key Takeaways — licensed spectrum is the correct choice specifically for an exclusive/interference-free use requirement, since it comes with exclusive purchased rights and legal recourse against interference (unlike unlicensed public bands).

- **A and B are wrong** — unlicensed bands are open to anyone, carrying real interference risk and no legal recourse — the opposite of what's required here.
- **D is wrong** — spectrum licensing status, not just range, is the deciding factor for this specific requirement.

---

## Missed-Concept Watchlist

No misses recorded — every lesson review and the Module Quiz scored 100% in the source notes.
