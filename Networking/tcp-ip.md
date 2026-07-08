# TCP/IP Model

## What is TCP/IP?

TCP/IP, or Transmission Control Protocol/Internet Protocol, is the networking model used by the Internet. It defines how data is transmitted between devices.

---

# The Four Layers of TCP/IP

## 1. Application Layer

Provides network services directly to user applications.

Examples:

- HTTP
- HTTPS
- FTP
- SSH
- DNS
- SMTP

Common activities:

- Browsing websites
- Sending emails
- Remote logins
- File transfers

---

## 2. Transport Layer

Responsible for end-to-end communication between devices.

### TCP

TCP is:

- Connection-oriented
- Reliable
- Error-checking
- Delivery-confirming

Examples:

- HTTPS
- SSH
- FTP

### UDP

UDP is:

- Connectionless
- Faster than TCP
- Not guaranteed to deliver data

Examples:

- DNS
- Video streaming
- Online gaming

---

## 3. Internet Layer

Responsible for routing packets across networks.

Protocols:

- IP
- ICMP
- ARP

Functions:

- Logical addressing
- Packet routing
- Path selection

---

## 4. Network Access Layer

Responsible for communication with the physical network.

Technologies:

- Ethernet
- Wi-Fi
- Fiber optic
- MAC addresses

Devices:

- Switches
- Network Interface Cards

---

# TCP/IP vs OSI Model

| TCP/IP Layer | OSI Equivalent |
|---|---|
| Application | Application, Presentation, Session |
| Transport | Transport |
| Internet | Network |
| Network Access | Data Link, Physical |

---

# Encapsulation Process

1. Application creates data.
2. Transport layer adds a TCP or UDP header.
3. Internet layer adds an IP header.
4. Network Access layer adds a frame header and trailer.
5. Data is transmitted across the network.

---

# Decapsulation Process

1. Network Access layer removes frame information.
2. Internet layer removes IP header.
3. Transport layer removes TCP or UDP header.
4. Application layer receives the original data.

---

# Example: Loading a Website

1. User enters a URL.
2. DNS resolves the domain name to an IP address.
3. TCP establishes a connection.
4. HTTP or HTTPS requests the webpage.
5. The server sends the response back to the client.

---

# Key Terms

| Term | Meaning |
|---|---|
| Packet | Unit of data at the Internet layer |
| Segment | Unit of data at the Transport layer |
| Frame | Unit of data at the Network Access layer |
| IP Address | Logical address assigned to a device |
| Port | Communication endpoint used by applications |

---

# Cybersecurity Relevance

TCP/IP knowledge is important for:

- Packet captures in Wireshark
- Firewall rules
- Network troubleshooting
- Port scanning with Nmap
- Detecting malicious traffic
- Understanding network attacks

Examples of attacks:

- Denial-of-Service
- TCP SYN Floods
- DNS attacks
- IP spoofing
- Man-in-the-Middle attacks

---

# Tools That Use TCP/IP Knowledge

- Wireshark
- Nmap
- tcpdump
- Burp Suite
- Ping
- Traceroute
- Netstat

---

# Lessons Learned

- The Internet operates using TCP/IP.
- Data is encapsulated and decapsulated as it travels.
- Different protocols operate at different layers.
- TCP/IP knowledge makes troubleshooting easier.
