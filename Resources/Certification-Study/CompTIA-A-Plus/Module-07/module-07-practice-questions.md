# Module 7 Practice Questions

*Supporting Network Services — CompTIA A+ Core 1 (220-1201)*

This module has explicit, named misses recorded in the source notes (7.1.12 at 93%, 7.2.8 at 90%, 7.3.7 at 93%) — these are the highest-priority review items in the whole module and are built out first below, followed by additional application questions from the Module Quiz and Checkpoint content.

---

## 7.1 — Networked Host Services (confirmed miss: AAA roles)

**Q1.** In an AAA (Authentication, Authorization, Accounting) setup, a laptop is trying to connect to a secured network. Which role does the laptop play, and which device relays the request without storing any credentials?

A. The laptop is the NAS/NAP; the switch is the Supplicant
B. The laptop is the Supplicant (device requesting access); the switch/AP is the NAS/NAP (relay only, never stores credentials)
C. The laptop is the AAA server; the switch is the Supplicant
D. Both the laptop and switch store credentials independently

**Correct: B.**
Why: This is the module's confirmed missed concept (7.1.12, scored 93%) — Supplicant = the device *requesting* access; NAS/NAP = the access appliance that only relays the request and never stores credentials itself (the actual AAA server does that). The notes explicitly flag these two roles as easy to mix up.

- **A reverses the two roles** — this is exactly the mix-up the source notes flag as the actual missed item.
- **C is wrong** — the AAA server is a separate backend system (e.g., a RADIUS/TACACS+ server), not the end-user's laptop.
- **D is wrong** — this defeats the entire purpose of AAA, which is to centralize credential storage in one place rather than on every access device.

---

**Q2.** What is the critical security difference between Telnet and SSH?

A. Telnet is encrypted but slower; SSH is unencrypted but faster
B. Telnet has zero security features (fully plaintext); SSH provides encrypted CLI access
C. They are functionally identical, differing only in port number
D. SSH is only used for file transfer, not CLI access

**Correct: B.**
Why: Stated directly in the 7.1.12 Key Takeaways — don't attribute SSH's encryption to Telnet; Telnet is explicitly plaintext for everything.

- **A reverses reality entirely.**
- **C is wrong** — they differ fundamentally in security model, not just port number (though the ports do differ too: Telnet TCP/23, SSH TCP/22).
- **D is wrong** — SSH provides secure CLI access as its primary function; SFTP (file transfer) is an *additional* capability it enables, not its only use.

---

**Q3.** A technician needs to configure LDAP on a directory server and accidentally opens port 3389 instead. What port should they have used, and why is this mix-up common?

A. Port 389 (LDAP) vs. port 3389 (RDP) — visually similar digit sequences make them easy to misread
B. Port 636 (LDAPS) vs. port 389 — both are LDAP variants
C. Port 25 vs. port 587 — both are mail ports
D. There is no meaningful difference; both ports work for LDAP

**Correct: A.**
Why: Stated directly in the 7.1.12 Key Takeaways as a specifically named point of confusion — LDAP (389) and RDP (3389) are visually similar and easy to misread.

- **B is wrong** — while 389 vs. 636 is a real LDAP/LDAPS distinction, it isn't the pairing named in the notes as the point of confusion here.
- **C is wrong** — 25/587 is a real SMTP-relay-vs-submission distinction from 7.1.5, but unrelated to this LDAP/RDP question.
- **D is wrong** — 389 (LDAP) and 3389 (RDP) are completely different protocols/services; using the wrong one would fail entirely.

---

## 7.2 — Internet and Embedded Appliances (confirmed miss: SCADA)

**Q4.** A utility company manages field devices (remote pumping stations) spread across an entire state. What communication method do these SCADA field devices use to reach the control system?

A. Local Wi-Fi
B. WAN, via cellular or satellite — not Wi-Fi
C. USB, connected directly to a technician's laptop during site visits
D. Bluetooth mesh networking

**Correct: B.**
Why: This is the module's confirmed missed concept (7.2.8, scored 90%) — SCADA field devices communicate via WAN (cellular/satellite) specifically because Wi-Fi is inherently local-range, and SCADA's whole point is multi-site/long-distance management.

- **A is wrong** — this is the actual missed answer; Wi-Fi's local range doesn't fit SCADA's multi-site design purpose at all.
- **C and D are wrong** — neither USB nor Bluetooth mesh offers the long-distance, unattended connectivity SCADA field devices require.
- **Test-taking cue from the notes:** when a question emphasizes "multiple sites" or "large-scale," think WAN-class technology, not local wireless.

---

**Q5.** A small business wants content filtering, spam filtering, antivirus, and an intrusion prevention system, but has a limited budget and wants centralized management. What's the best-fit device?

A. A standalone firewall only
B. UTM (Unified Threat Management)
C. A proxy server only
D. Four separate single-function appliances

**Correct: B.**
Why: Stated directly in the 7.2.8 Key Takeaways — UTM is explicitly the correct answer whenever a scenario lists multiple distinct security needs on a budget, versus picking one single-function device.

- **A and C are wrong** — each only covers one of the listed needs (firewall = ACL-based filtering only; proxy = caching + request inspection only), leaving the others unaddressed.
- **D is wrong** — this technically covers all needs but ignores the stated budget and centralized-management requirements, which UTM is specifically designed to solve by consolidating functions into one appliance.

---

**Q6.** What specifically distinguishes a proxy server from simple NAT?

A. A proxy only translates IP addresses, same as NAT
B. A proxy inspects the entire request and reply (not just addresses) and can cache content — NAT only translates addresses
C. NAT works for HTTP only; proxies work for all protocols
D. There is no meaningful difference between the two

**Correct: B.**
Why: Stated directly in the 7.2.8 Key Takeaways — a proxy server's specific signature is caching + full request/reply inspection, explicitly distinct from NAT-style address translation alone.

- **A is wrong** — this describes NAT's function, not what makes a proxy different from it.
- **C is wrong** — reverses reality: NAT is protocol-agnostic address translation; proxies (in this context) are described in relation to HTTP and other protocols they can inspect.
- **D is wrong** — the notes draw a clear functional distinction between the two.

---

## 7.3 — Troubleshoot Networks (confirmed miss: scope of the problem)

**Q7.** Every user on an entire office network reports slow file transfers simultaneously. Where should troubleshooting focus first?

A. Each individual user's laptop hardware
B. Shared infrastructure (switch/router), since the whole network is affected — not individual host hardware
C. Reinstalling the OS on the most vocal complainant's machine
D. Replacing NICs on all affected machines

**Correct: B.**
Why: This is the module's confirmed missed concept (7.3.7, scored 93%) — a network-wide slowdown affecting ALL users points to shared infrastructure congestion, not individual host hardware. The core principle reinforced throughout the lesson: scope tells you where to look (one user → check that host; one switch → check that switch; whole network → check shared infrastructure).

- **A and D are wrong** — this is the actual missed answer pattern; individual-host troubleshooting doesn't match a symptom affecting every user simultaneously.
- **C is wrong** — reinstalling one OS addresses at most one machine, ignoring that the entire network is affected.

---

**Q8.** A network analyzer reports rising damaged frame counts on a segment. What does this specifically indicate, as opposed to duplex mismatch or outdated drivers?

A. External interference
B. A software licensing issue
C. A misconfigured DNS server
D. An expired IP lease

**Correct: A.**
Why: Stated directly in the Module 7 Quiz Key Takeaways — damaged frame counts are the specific tell for external interference, explicitly distinguished from duplex mismatch, bad termination, or outdated drivers, which each have their own separate symptom signatures.

- **B, C, D are wrong** — none of these relate to frame-level damage on the physical/data-link layer; they're software/addressing-layer issues with entirely different symptoms.

---

## Checkpoint Quiz (Cumulative Review, Modules 1-7)

**Q9.** A monitor shows several small black dots that never change regardless of what's displayed. What's the correct next step?

A. Adjust brightness/contrast settings
B. Check for warranty replacement — these are likely dead pixels, generally not repairable
C. Update the graphics driver
D. Replace the video cable

**Correct: B.**
Why: Stated directly in the Checkpoint Quiz Key Takeaways — static black dots regardless of content are dead pixels, generally not repairable, so warranty replacement is the correct path (distinct from a *stuck* pixel, which is sometimes fixable via cycling software or a gentle tap, per 4.3.7).

- **A, C, D are wrong** — none of these fix a hardware-level dead pixel; brightness/driver/cable issues would affect the whole display, not isolated permanent dots.

---

**Q10.** Two new HDDs are installed, but only one shows a drive letter in File Explorer. What should be checked FIRST?

A. Assume hardware failure and replace the second drive
B. Check Windows Disk Management first — it likely just needs initializing/formatting
C. Reseat the drive's SATA data cable
D. Run a full S.M.A.R.T. diagnostic

**Correct: B.**
Why: Stated directly in the Checkpoint Quiz Key Takeaways — this is explicitly the first check, since a brand-new drive with no assigned letter is very commonly just uninitialized/unformatted, not faulty.

- **A is wrong** — jumping straight to hardware replacement skips the much more common and easily-fixed software-level cause.
- **C and D are wrong** — these are reasonable *later* steps if Disk Management shows the drive isn't even detected, but they're not the notes' identified first check for this specific symptom (drive IS presumably detected by the system, just has no assigned letter/format).

---

## Missed-Concept Watchlist

- **7.1.12 (scored 93%):** AAA roles — Supplicant (device requesting access) vs. NAS/NAP (relay only, never stores credentials). See Q1.
- **7.2.8 (scored 90%):** SCADA field devices communicate over WAN (cellular/satellite), not Wi-Fi — a "multiple sites/large-scale" scenario should always cue WAN-class thinking. See Q4.
- **7.3.7 (scored 93%):** Scope determines where to troubleshoot — a network-wide symptom (all users affected) means checking shared infrastructure, not individual host hardware. See Q7.
