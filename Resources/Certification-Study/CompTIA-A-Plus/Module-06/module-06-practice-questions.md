# Module 6 Practice Questions

*Configuring Network Addressing and Internet Connections — CompTIA A+ Core 1 (220-1201)*

Two lesson reviews in this module had a confirmed real miss (6.1.11 scored 73%, retaken to 93%; 6.2.16 scored 93%) — the source notes don't specify exactly which individual question was missed on either, only the consolidated takeaways, so those are treated as high-priority review material below rather than confirmed "missed items."

---

## 6.1 — Internet Connection Types

**Q1.** An ISP technician is diagnosing a connection type where a signal travels via ground-to-ground antennas rather than to orbit. What connection type is this?

A. Satellite
B. WISP (fixed wireless)
C. FTTC
D. Cable (HFC)

**Correct: B — WISP.**
Why: Stated directly in the 6.1.11 Key Takeaways — antenna-to-antenna microwave signal (ground-to-ground) is WISP, distinct from satellite (ground-to-orbit). This is flagged as a real point of confusion worth extra review given the lesson's lower first-attempt score.

- **A is wrong** — satellite is specifically ground-to-orbit, the opposite of this scenario.
- **C is wrong** — FTTC (fiber to the curb/cabinet) relies on fiber + copper (VDSL), not microwave antennas.
- **D is wrong** — cable/HFC uses coax + fiber backbone, not point-to-point wireless antennas.

---

**Q2.** A customer wants the fastest, most reliable internet option and full fiber is available to their building. What should be recommended, and why is it superior to the copper-finish alternative?

A. FTTC — because copper is cheaper to maintain
B. FTTP — no copper involved at all, unlike FTTC which stops at a cabinet and finishes over copper (VDSL)
C. ADSL — because it's the most widely available
D. DOCSIS cable — because it uses coax exclusively

**Correct: B — FTTP.**
Why: Stated directly in the 6.1.11 Key Takeaways — FTTP wins for max speed/reliability specifically because it's fiber all the way to the premises, with FTTC's remaining copper stretch (VDSL) as the bottleneck by comparison.

- **A is wrong** — cost isn't the deciding factor asked about, and FTTC's copper segment is precisely its limitation, not an advantage.
- **C is wrong** — ADSL is explicitly the oldest/slowest wired option in the notes, not a "fastest/most reliable" recommendation.
- **D is wrong** — DOCSIS/cable is HFC (fiber + coax), a different technology from fiber-to-premises, and isn't the fastest/most reliable option when true FTTP is available.

---

**Q3.** What is the functional difference between a modem and a router, even though SOHO devices often combine both into one box?

A. They are the same function under two names
B. Modem = physical WAN connection only; Router = logical forwarding via IP
C. Router = physical WAN connection only; Modem = logical forwarding via IP
D. A modem requires an IP address; a router does not

**Correct: B.**
Why: Stated directly in the 6.1.11 Key Takeaways — this distinction is explicitly called out as something not to confuse, even though SOHO devices bundle both functions into one physical unit.

- **A is wrong** — this is the exact confusion the takeaway warns against.
- **C reverses the correct roles.**
- **D is wrong** — routers are the IP-forwarding devices requiring IP configuration; a modem's role is the physical WAN link, not IP logic.

---

## 6.2 — TCP/IP Concepts

**Q4.** A host's IPv6 address begins with `2001:0db8::...`. Which 64 bits identify the specific subnet this host belongs to?

A. The last 64 bits (Interface ID)
B. The first 64 bits (Network ID)
C. Subnet identification requires a separate subnet mask, same as IPv4
D. IPv6 doesn't use subnetting at all

**Correct: B.**
Why: Stated directly in the 6.2.16 Key Takeaways — IPv6 subnet identification comes from the network ID (first 64 bits), NOT the interface ID (last 64 bits) — flagged as the specific point worth extra review given this lesson's 93% score.

- **A is wrong** — this is the exact reversal the takeaway warns against; the Interface ID identifies the specific host, not the subnet.
- **C is wrong** — IPv6 doesn't use a separate subnet mask the way IPv4 does; the fixed 64/64 split (Network ID / Interface ID) serves that role structurally.
- **D is wrong** — IPv6 absolutely subnets, via its structured address format.

---

**Q5.** A router has correct IP addressing configured on all interfaces, but traffic still isn't being forwarded between networks. What is a separate setting worth checking?

A. Whether IPv4 forwarding is enabled — a distinct setting that can be disabled independently of correct addressing
B. Whether the DNS server is reachable
C. Whether DHCP is running
D. Whether the router has a valid MAC address

**Correct: A.**
Why: Stated directly in the 6.2.16 Key Takeaways — IPv4 forwarding is called out as a distinct router setting that can be off even when addressing itself is fully correct, which is exactly the trap in this scenario.

- **B and C are wrong** — DNS and DHCP govern name resolution and address assignment, not the router's core packet-forwarding function between networks.
- **D is wrong** — every network interface has a MAC address by default; that's not a variable setting worth troubleshooting here.

---

**Q6.** What tool provides secure remote access into a network over the public internet?

A. NAT
B. VPN
C. APIPA
D. DHCP Relay

**Correct: B.**
Why: Stated directly in the 6.2.16 Key Takeaways.

- **A is wrong** — NAT translates private addresses for outbound internet access; it doesn't provide secure remote *access into* a network.
- **C is wrong** — APIPA is a DHCP-failure fallback self-addressing mechanism, unrelated to remote access.
- **D is wrong** — DHCP Relay forwards DHCP requests to a separate server; it has nothing to do with secure remote access.

---

## 6.3 — Network Communications

**Q7.** A client sends packets that reach the server, but no response ever comes back on the expected port. What is the likely explanation?

A. The client's cable is faulty
B. The server is likely listening on a different port than expected
C. DNS resolution has failed
D. The packets were lost in transit and never arrived

**Correct: B.**
Why: Stated directly in the 6.3.7 Key Takeaways (100% score, confirmed content).

- **A is wrong** — if packets are confirmed reaching the server, the cable/physical layer isn't the issue.
- **C is wrong** — DNS failure would prevent the connection from being established at all (no destination IP resolved), not result in packets reaching the server with no response.
- **D is wrong** — the scenario states the packets DO reach the server; this contradicts "lost in transit."

---

**Q8.** During a TCP handshake, the client sends SYN, receives SYN/ACK back, but the final ACK never seems to register with the server. What is the classic symptom this indicates?

A. Normal, expected behavior — no issue exists
B. A firewall blocking the connection
C. The server is out of available ports
D. DNS misconfiguration

**Correct: B.**
Why: Stated directly in the 6.3.7 Key Takeaways — a handshake stalling after SYN/ACK, before the final ACK, is called out as a classic firewall-blocking symptom.

- **A is wrong** — a stalled handshake is not normal; the three-way handshake should complete cleanly.
- **C is wrong** — port exhaustion isn't the notes' identified cause for this specific stalling pattern.
- **D is wrong** — DNS operates before the handshake (resolving the address); it wouldn't cause a stall mid-handshake.

---

## 6.4 — Network Configuration Concepts

**Q9.** A DNS query returns "NXDOMAIN." What does this specifically mean?

A. The DNS server is unreachable (timeout)
B. The domain itself doesn't exist or isn't registered
C. The DNS server is misconfigured
D. The requested record type isn't supported

**Correct: B.**
Why: Stated directly in the 6.7 Module Quiz Key Takeaways (100% score) — NXDOMAIN is explicitly distinguished from a DNS server being unreachable, which would instead produce a timeout, not an NXDOMAIN response.

- **A is wrong** — this describes a timeout, a different failure mode the takeaway explicitly contrasts against NXDOMAIN.
- **C and D are wrong** — neither matches the specific defined meaning of an NXDOMAIN response, which is about domain existence, not server config or record type.

---

## Missed-Concept Watchlist

- **6.1.11 (scored 73% → 93% after retake):** A real miss occurred here, but the source notes only capture the consolidated corrected takeaways (WISP vs. satellite, FTTP vs. FTTC, modem vs. router — see Q1-Q3 above), not which specific question was originally missed. Treat all three as high-priority review material.
- **6.2.16 (scored 93%):** Same situation — a miss occurred, takeaways captured (IPv6 subnet ID, IPv4 forwarding as a separate setting, VPN's role — see Q4-Q6 above), specific missed question not recorded.
