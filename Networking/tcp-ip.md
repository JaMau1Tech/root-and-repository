# TCP/IP Model

## What is TCP/IP?

TCP/IP (Transmission Control Protocol/Internet Protocol) is the networking model used by the Internet. It defines how data is transmitted between devices on a network.

---

# The Four Layers of the TCP/IP Model

## 1. Application Layer

Provides network services directly to user applications.

### Examples
- HTTP
- HTTPS
- FTP
- SSH
- DNS
- SMTP

### Common Activities
- Browsing websites
- Sending emails
- Remote logins
- File transfers

---

## 2. Transport Layer

Responsible for end-to-end communication between devices.

### Protocols

#### TCP (Transmission Control Protocol)
- Connection-oriented
- Reliable
- Performs error checking
- Guarantees delivery

Examples:
- HTTPS
- SSH
- FTP

#### UDP (User Datagram Protocol)
- Connectionless
- Faster than TCP
- No guarantee of delivery

Examples:
- DNS
- Video streaming
- Online gaming

---

## 3. Internet Layer

Responsible for routing packets across networks.

### Protocols
- IP
- ICMP
- ARP

### Functions
- Logical addressing
- Packet routing
- Determining the best path to a destination

---

## 4. Network Access Layer

Responsible for communication with the physical network.

### Technologies
- Ethernet
- Wi-Fi
- Fiber Optic
- MAC Addresses

### Devices
- Switches
- Network Interface Cards (NICs)

---

# TCP/IP vs OSI Model

| TCP/IP Layer | OSI Equivalent |
|--------------|----------------|
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

# Example: Loading a Website

1. User enters a URL.
2. DNS resolves the domain name to an IP address.
3. TCP establishes a connection.
4. HTTP/HTTPS requests the webpage.
5. The server sends the response back to the client.

---

# Key Terms

- Packet: Unit of data at the Internet layer.
- Segment: Unit of data at the Transport layer.
- Frame: Unit of data at the Network Access layer.
- IP Address: Logical address assigned to a device.
- Port: Communication endpoint used by applications.

---

# Notes

Understanding the TCP/IP model is fundamental for:
- Networking
- Cybersecurity
- Packet analysis
- Troubleshooting
- Penetration testing