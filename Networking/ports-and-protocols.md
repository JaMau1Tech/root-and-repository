# Common Ports and Protocols

Understanding common ports and protocols is essential for networking, system administration, and cybersecurity.

---

# Common Ports

| Port | Protocol | Purpose |
|------|-----------|----------|
| 20/21 | FTP | File Transfer |
| 22 | SSH | Secure Remote Login |
| 23 | Telnet | Remote Access |
| 25 | SMTP | Email Sending |
| 53 | DNS | Domain Name Resolution |
| 67/68 | DHCP | Dynamic IP Assignment |
| 80 | HTTP | Web Traffic |
| 110 | POP3 | Email Retrieval |
| 143 | IMAP | Email Retrieval |
| 443 | HTTPS | Secure Web Traffic |
| 3389 | RDP | Remote Desktop |

---

# Protocol Descriptions

## FTP (File Transfer Protocol)

**Ports:** 20 and 21

Purpose:
- Transfers files between computers.

Security Note:
- Sends data in plaintext.
- Not considered secure.

Secure Alternative:
- SFTP
- SCP

---

## SSH (Secure Shell)

**Port:** 22

Purpose:
- Secure remote administration.
- Command-line access to servers.

Security Note:
- Encrypts communications.
- Widely used by system administrators and cybersecurity professionals.

---

## Telnet

**Port:** 23

Purpose:
- Remote command-line access.

Security Note:
- Sends usernames and passwords in plaintext.
- Rarely used today because it is insecure.

Secure Alternative:
- SSH

---

## SMTP (Simple Mail Transfer Protocol)

**Port:** 25

Purpose:
- Sends email between mail servers.

---

## DNS (Domain Name System)

**Port:** 53

Purpose:
- Converts domain names into IP addresses.

Example:

```text
google.com → 142.250.x.x
```

---

## DHCP (Dynamic Host Configuration Protocol)

**Ports:** 67 and 68

Purpose:
- Automatically assigns:

  - IP addresses
  - Subnet masks
  - Default gateways
  - DNS servers

---

## HTTP (Hypertext Transfer Protocol)

**Port:** 80

Purpose:
- Transfers web pages.

Security Note:
- Unencrypted.

---

## HTTPS (Hypertext Transfer Protocol Secure)

**Port:** 443

Purpose:
- Secure web communication.

Security Features:
- Encryption
- Authentication
- Data integrity

Uses:
- Banking websites
- Online shopping
- Secure logins

---

## POP3 (Post Office Protocol Version 3)

**Port:** 110

Purpose:
- Downloads emails from a server.

---

## IMAP (Internet Message Access Protocol)

**Port:** 143

Purpose:
- Synchronizes email across multiple devices.

---

## RDP (Remote Desktop Protocol)

**Port:** 3389

Purpose:
- Provides remote access to Windows systems.

Security Note:
- Frequently targeted by attackers.
- Should be secured with:
  - Strong passwords
  - Multi-factor authentication
  - VPN access

---

# Ports Frequently Seen in Cybersecurity

| Port | Why It Matters |
|------|----------------|
| 22 | Remote administration |
| 53 | DNS attacks and troubleshooting |
| 80 | Web servers |
| 443 | Secure web applications |
| 3389 | Common attack target |
| 21 | Insecure file transfer |
| 23 | Insecure remote access |

---

# Common Commands

## Windows

```powershell
netstat -ano
```

Displays active network connections.

---

## Linux

```bash
ss -tulnp
```

Displays listening ports and services.

```bash
netstat -tulnp
```

Displays active connections and listening ports.

---

# Cybersecurity Relevance

Understanding ports and protocols is important for:

- Network troubleshooting
- Firewall configuration
- Vulnerability scanning
- Port scanning with Nmap
- Incident response
- Packet analysis with Wireshark
- Penetration testing

---

# Lessons Learned

- Every service typically communicates on a specific port.
- Open ports can represent both functionality and risk.
- Understanding protocols helps identify abnormal network activity.
- Many cybersecurity tools rely heavily on port and protocol knowledge.