# OSI Model

The OSI Model is a conceptual framework used to understand how data travels across a network. It divides network communication into seven layers.

---

# Layer 7 - Application

## Purpose

Provides network services directly to applications and users.

## Examples

- HTTP
- HTTPS
- FTP
- DNS
- SMTP

## Devices

- Web servers
- Mail servers

---

# Layer 6 - Presentation

## Purpose

Handles:

- Data formatting
- Encryption
- Compression

## Examples

- SSL
- TLS
- JPEG
- PNG
- ASCII

---

# Layer 5 - Session

## Purpose

Creates, manages, and terminates communication sessions between devices.

## Examples

- RPC
- NetBIOS
- SMB sessions

---

# Layer 4 - Transport

## Purpose

Provides end-to-end communication and controls reliability.

## Protocols

- TCP
- UDP

## Functions

- Error checking
- Flow control
- Segmentation

---

# Layer 3 - Network

## Purpose

Responsible for logical addressing and routing packets between networks.

## Protocols

- IP
- ICMP
- IPSec

## Devices

- Routers
- Layer 3 switches

---

# Layer 2 - Data Link

## Purpose

Responsible for:

- MAC addressing
- Frame delivery
- Error detection

## Devices

- Switches
- Network Interface Cards

## Protocols

- Ethernet
- PPP

---

# Layer 1 - Physical

## Purpose

Transmits raw bits across physical media.

## Examples

- Ethernet cables
- Fiber optic cables
- Wireless signals
- Connectors

## Devices

- Hubs
- Repeaters
- Cables

---

# OSI Mnemonics

Top to bottom:

```text
All People Seem To Need Data Processing
```

Bottom to top:

```text
Please Do Not Throw Sausage Pizza Away
```

---

# Example: Loading a Website

| Layer | Example |
|---|---|
| 7 | HTTPS request |
| 6 | TLS encryption |
| 5 | Session established |
| 4 | TCP connection |
| 3 | IP addressing |
| 2 | Ethernet frame |
| 1 | Electrical or wireless signal |

---

# Cybersecurity Relevance

Understanding the OSI model helps with:

- Network troubleshooting
- Packet analysis
- Firewall configuration
- Wireshark analysis
- Vulnerability assessment
- Understanding attacks at different layers

Examples:

| Attack or Issue | OSI Layer |
|---|---|
| Phishing | Layer 7 |
| TLS issues | Layer 6 |
| TCP SYN flood | Layer 4 |
| IP spoofing | Layer 3 |
| ARP spoofing | Layer 2 |

---

# Lessons Learned

- Network communication uses multiple layers.
- Problems can occur at any layer.
- The OSI model helps organize troubleshooting.
- Cybersecurity tools often analyze traffic by layer.
