# Common Ports and Protocols

Understanding common ports and protocols is essential for networking, system administration, and cybersecurity.

---

# Common Ports

| Port | Protocol | Purpose |
|---:|---|---|
| 20/21 | FTP | File Transfer |
| 22 | SSH | Secure Remote Login |
| 23 | Telnet | Remote Access |
| 25 | SMTP | Email Sending |
| 53 | DNS | Domain Name Resolution |
| 67/68 | DHCP | Dynamic IP Assignment |
| 69 | TFTP | Simple File Transfer |
| 80 | HTTP | Web Traffic |
| 88 | Kerberos | Authentication |
| 110 | POP3 | Email Retrieval |
| 123 | NTP | Time Synchronization |
| 143 | IMAP | Email Retrieval |
| 161 | SNMP | Network Management |
| 389 | LDAP | Directory Services |
| 443 | HTTPS | Secure Web Traffic |
| 445 | SMB | Windows File Sharing |
| 514 | Syslog | Log Forwarding |
| 636 | LDAPS | Secure Directory Services |
| 3389 | RDP | Remote Desktop |

---

# Protocol Descriptions

## FTP

Ports:

```text
20/21
```

Purpose:

- Transfers files between computers.

Security note:

- Sends data in plaintext.
- Not considered secure.

Secure alternatives:

- SFTP
- SCP

---

## SSH

Port:

```text
22
```

Purpose:

- Secure remote administration
- Command-line access to servers

Security note:

- Encrypts communication
- Widely used by system administrators and cybersecurity professionals

---

## Telnet

Port:

```text
23
```

Purpose:

- Remote command-line access

Security note:

- Sends usernames and passwords in plaintext.
- Replaced by SSH in most environments.

---

## DNS

Port:

```text
53
```

Purpose:

- Converts domain names into IP addresses.

Example:

```text
example.com -> IP address
```

---

## HTTP and HTTPS

Ports:

```text
80
443
```

Purpose:

- HTTP transfers web pages.
- HTTPS secures web communication using encryption.

---

## SMB

Port:

```text
445
```

Purpose:

- Windows file sharing
- Printer sharing
- Network resource access

Security note:

- Commonly targeted by attackers.
- Should not be exposed directly to the internet.

---

## RDP

Port:

```text
3389
```

Purpose:

- Remote desktop access to Windows systems.

Security note:

- Common attack target.
- Should be protected with MFA, VPN access, and strong passwords.

---

# Useful Commands

## Windows

```powershell
netstat -ano
```

Displays active network connections.

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

Ports and protocols are important for:

- Network troubleshooting
- Firewall configuration
- Vulnerability scanning
- Port scanning with Nmap
- Incident response
- Packet analysis with Wireshark
- Penetration testing

---

# Lessons Learned

- Services usually communicate on specific ports.
- Open ports can represent functionality and risk.
- Protocol knowledge helps identify abnormal network activity.
- Many cybersecurity tools rely on port and protocol knowledge.
