# Module 06 – How The Web Works

## Overview

This module introduces the technologies that power modern websites and web applications. It explains how DNS resolves domain names, how HTTP and HTTPS enable communication between browsers and servers, how websites are built using client-side and server-side technologies, and how these components work together to deliver web content securely.

Understanding these technologies provides the foundation for web application security, penetration testing, vulnerability assessment, and future learning throughout the TryHackMe Pre Security path.

---

## Module Objectives

- Understand the purpose of DNS
- Understand HTTP and HTTPS communication
- Learn how websites are built
- Understand front-end and back-end technologies
- Learn common web security concepts
- Build a strong foundation for web application security

---

# Rooms

| Status | Room | Description |
|---------|------|-------------|
| ✅ | DNS in Detail | Learn how DNS translates domain names into IP addresses. |
| ✅ | HTTP in Detail | Learn how browsers communicate with web servers using HTTP and HTTPS. |
| ✅ | How Websites Work | Learn how websites are built and introduce common web security concepts. |
| ⬜ | Putting it all together | Review and combine DNS, HTTP, and website technologies into the complete web request lifecycle. |

---

# Skills Learned

## DNS Fundamentals

- Domain Name System (DNS)
- Domain Hierarchy
- Root Domains
- Top-Level Domains (TLD)
- Generic Top-Level Domains (gTLD)
- Country Code Top-Level Domains (ccTLD)
- Second-Level Domains
- Subdomains
- DNS Resolution
- DNS Caching
- Time To Live (TTL)

---

## DNS Record Types

- A Records
- AAAA Records
- CNAME Records
- MX Records
- TXT Records

---

## HTTP & HTTPS

- HyperText Transfer Protocol
- HyperText Transfer Protocol Secure
- TLS Encryption
- URLs
- URL Components
- HTTP Requests
- HTTP Responses
- HTTP Headers
- HTTP Cookies
- Sessions
- Browser Communication

---

## HTTP Methods

- GET
- POST
- PUT
- DELETE

---

## HTTP Status Codes

- 1xx Informational
- 2xx Success
- 3xx Redirection
- 4xx Client Errors
- 5xx Server Errors

Common Codes

- 200 OK
- 201 Created
- 301 Moved Permanently
- 302 Found
- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden
- 404 Not Found
- 405 Method Not Allowed
- 500 Internal Server Error
- 503 Service Unavailable

---

## Web Technologies

### Front-End

- HTML
- JavaScript
- DOM
- Browser Rendering
- Client-Side Processing

### Back-End

- Web Servers
- Server-Side Processing
- Databases
- APIs
- Authentication

---

## Web Security Concepts

- Source Code Review
- Sensitive Data Exposure
- HTML Injection
- Input Validation
- Input Sanitization
- Output Encoding

---

## Practical Skills

### DNS

- DNS Enumeration
- Querying DNS Records
- DNS Lookup Tools
- Understanding DNS Responses

### HTTP

- Building GET Requests
- Building POST Requests
- Building PUT Requests
- Building DELETE Requests
- Configuring URI Parameters
- Configuring Body Parameters
- Reading HTTP Headers
- Analyzing HTTP Responses

### Website Analysis

- Reading HTML
- Editing HTML
- Viewing Page Source
- JavaScript Manipulation
- DOM Manipulation
- Credential Discovery
- HTML Injection

---

# Completed Rooms

## ✅ DNS in Detail

### Overview

Learned how DNS translates domain names into IP addresses and how DNS requests travel across the Internet.

### Topics Covered

- What DNS is
- Domain Hierarchy
- DNS Record Types
- DNS Resolution Process
- DNS Caching
- TTL
- Practical DNS Queries

### Documentation

```text
DNS-in-Detail/task-notes.md
```

### Screenshots

**6**

---

## ✅ HTTP in Detail

### Overview

Learned how browsers communicate with web servers using HTTP and HTTPS.

### Topics Covered

- HTTP
- HTTPS
- URLs
- Requests
- Responses
- HTTP Methods
- Status Codes
- Headers
- Cookies
- Practical HTTP Requests

### Documentation

```text
HTTP-in-Detail/task-notes.md
```

### Screenshots

**8**

---

## ✅ How Websites Work

### Overview

Learned how websites are built using front-end and back-end technologies while introducing fundamental web security concepts.

### Topics Covered

- Website Architecture
- Front-End
- Back-End
- HTML
- JavaScript
- Sensitive Data Exposure
- HTML Injection

### Documentation

```text
How-Websites-Work/task-notes.md
```

### Screenshots

**6**

---

# Screenshots

All screenshots for this module are stored in:

```text
images/
```

The complete screenshot index is documented in:

```text
images/README.md
```

### Screenshot Summary

| Room | Screenshots |
|------|------------:|
| DNS in Detail | 6 |
| HTTP in Detail | 8 |
| How Websites Work | 6 |
| Putting it all together | 0 |
| **Total** | **20** |

---

# Repository Structure

```text
Module-06-How-The-Web-Works/
│
├── README.md
│
├── images/
│   ├── README.md
│   ├── 20 screenshots
│
├── DNS-in-Detail/
│   └── task-notes.md
│
├── HTTP-in-Detail/
│   └── task-notes.md
│
├── How-Websites-Work/
│   └── task-notes.md
│
└── Putting-it-all-Together/
    └── task-notes.md
```

---

# Module Progress

| Room | Status |
|------|:------:|
| DNS in Detail | ✅ |
| HTTP in Detail | ✅ |
| How Websites Work | ✅ |
| Putting it all together | ⬜ |

**Rooms Completed:** **3 / 4**

**Module Completion:** **75%**

```text
██████████████████░░░░░░ 75%
```

---

# Next Room

## ➜ Putting it all together

The final room reviews and reinforces everything learned throughout Module 06 by combining DNS, HTTP, website technologies, and web request processing into one complete overview before progressing to **Module 07 – Attacks and Defenses**.

---

# Module Status

🟨 **In Progress**

**Completed Rooms:** 3

**Remaining Rooms:** 1

---

# Module Summary

By completing this module, you will understand:

- How browsers locate websites
- How HTTP communication works
- How websites are constructed
- The relationship between front-end and back-end technologies
- Fundamental web security concepts
- The complete lifecycle of a web request

These concepts provide the foundation for future web application security topics, including authentication, injection attacks, cross-site scripting (XSS), API security, and the OWASP Top 10.