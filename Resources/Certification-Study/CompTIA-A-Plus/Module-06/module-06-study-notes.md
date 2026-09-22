# Module 6 Study Notes

*Configuring Network Addressing and Internet Connections — CompTIA A+
Core 1 (220-1201)*

## 6.1 — Internet Connection Types

### 6.1.1 — Internet Connection Types and Modems

- Internet = network of networks; backbone = fiber + IXPs; ISPs
    connect via transit/peering in a tiered hierarchy

- Customer connects to ISP's nearest PoP; WAN link = point-to-point,
    uses a digital modem (not NIC/switch)

- Router + IP = identifies networks, forwards data between them
    (private LAN ↔ public Internet)

- Wired: DSL (phone lines, oldest/slowest), Cable (coax, faster),
    Fiber (new cable, light signals, fastest)

- Wireless: Satellite (global, slow/delayed, weather-sensitive), Fixed
    wireless (short-distance antennas, needs line of sight), Cellular
    (mobile 4G/5G)

### 6.1.2 — Digital Subscriber Line Modems

- PSTN core = fiber; PSTN edge = legacy copper = POTS/'local
    loop'/'last mile'

- DSL uses higher frequencies on copper phone lines; modulation + echo
    cancelling = high-bandwidth full-duplex

- ADSL = asymmetrical (fast down, slow up); ADSL2+ = ~24Mbps
    down/1.4-3.3Mbps up

- Symmetric DSL = equal up/down; better for business/branch
    upstream-heavy use

- DSL modem: RJ11 (phone line/WAN side) + RJ45 (router/LAN side)

- Splitter/filter separates voice and data at each phone socket

### 6.1.3 — Cable Modems

- Cable Internet = part of CATV; network = HFC (fiber core + coax to
    premises)

- DOCSIS = governing standard; base speeds ~43-56Mbps down/~31Mbps
    up; DOCSIS 4 = up to 10Gbps down/6Gbps up

- Cable modem: RJ45 → router (LAN); coax + F-type connector → ISP
    (WAN)

- ⚠ F-type = screw-down, don't overtighten

- Path: modem → CMTS (aggregates neighborhood) → fiber backbone → ISP
    PoP → Internet

### 6.1.5 — Fiber to the Curb and Fiber to the Premises

- Last mile copper = main bandwidth bottleneck; FTTx = umbrella term
    for fiber upgrade projects

- FTTC = fiber to a shared cabinet, copper (VDSL) for final stretch

- VDSL @ 300m: asymmetric 52/16 Mbps, symmetric 26/26 Mbps;
    VDSL2-Vplus @ 250m: 300/100 Mbps

- ⚠ ADSL modems ≠ VDSL modems; VDSL modems usually support ADSL

- FTTP = fiber all the way to the building, implemented as a PON (OLT
    → splitter → ONT)

- ONT converts optical→electrical; connects to router via RJ45; may
    have router built-in

- ONT's 'LOS' indicator = specifically reports the PON/fiber-side
    connection status

### 6.1.7 — Fixed Wireless Internet Access

- Geostationary satellite: huge coverage, 2-6Mbps up/30Mbps down,
    600-800ms RTT latency — bad for real-time apps

- VSAT dish points at fixed satellite position; no realignment needed;
    coax → DVB-S modem

- LEO satellite: better bandwidth (5-220Mbps), lower latency (25-60ms
    RTT); satellites move → motorized/phased-array/flat-panel antenna

- WISP = ground-based fixed wireless; directional antenna; licensed or
    unlicensed frequencies

- ⚠ All microwave radio links vulnerable to snow/rain/wind/solar
    flares

### 6.1.8 — Cellular Radio Internet Connections

- 3G: base station = 'cell,' up to 5mi/8km range; GSM (removable
    SIM) vs CDMA (no SIM, provider-managed)

- Status codes: G/E/1X = minimal (50-400Kbps); 3G(UMTS/EV-DO) ≈3Mbps;
    H/H+(HSPA/HSPA+) up to 42Mbps

- 4G = LTE, converged GSM+CDMA standard, requires SIM; max ~300Mbps

- 5G = wide spectrum (low band = range/penetration; mmWave = short
    range, no wall penetration); up to 10Gbps

- 5G uses mMIMO = many small antennas + multipath/beamforming

- 4G/5G also used for fixed-access home/business broadband and IoT

### 6.1.9 — Routers

- Switch forwards frames via MAC (hardware/port identity); Router
    forwards packets via IP (network + host identity)

- SOHO router = simple, one local + one WAN interface

- Enterprise: LAN router = splits into subnets/broadcast domains;
    WAN/border router = Ethernet + modem interface

- Router components: ventilation ports, WAN port, reset button (erases
    config), wireless antenna, Power LED, PoE status LED, Link lights
    per port

### 6.1.10 — Firewalls

- Firewall filters allowed/denied hosts and protocol types; rules =
    ACL (source/dest address + protocol + allow/block)

- Firewalls can be placed within a private network too, not just at
    the public/private boundary

- Router-integrated (basic) vs standalone appliance (deeper analysis,
    often UTM) vs personal/software firewall (single computer)

- Analogy: firewall = security guard at the gate; server = the
    warehouse

**6.1.11 Lesson Review — Key Takeaways (73% → 93% after retake)**

- ADSL config uses filters/splitters — NOT RG6/F-type (that's
    cable, not DSL)

- FTTP = full fiber to premises (no copper); FTTC stops at a cabinet,
    finishes over copper (VDSL) — FTTP wins for max speed/reliability

- Antenna-to-antenna microwave signal (ground-to-ground) = WISP, not
    satellite (satellite = ground-to-orbit)

- FTTC and FTTP both rely on fiber — NOT coax (coax = cable/HFC
    only)

- Modem = physical WAN connection only; Router = logical forwarding
    via IP — don't confuse the two even though SOHO devices combine
    both

## 6.2 — TCP/IP Concepts

### 6.2.1 — TCP/IP

- Protocol = rules for structured communication; protocol suite =
    multiple protocols working together (TCP/IP dominant)

- 4 layers (top→bottom): Application → Transport → Internet →
    Link/Network Interface

- Application layer: DHCP, DNS, FTP, HTTP/HTTPS, SMB, SMTP, IMAP,
    POP3, SSH, RDP, Telnet, LDAP, SNMP, Syslog

- Transport layer: TCP and UDP; Internet layer: IP (+ARP); Link layer:
    Ethernet, Wi-Fi

### 6.2.2 — Link or Network Interface Layer

- Puts frames onto the physical network; doesn't contain TCP/IP
    protocols itself

- Includes Ethernet, Wi-Fi (local) + DSL/cable modems (WAN interfaces)

- Communication scope = local network segment ONLY; data unit = frame;
    addressing = MAC address

### 6.2.3 — Internet Layer

- IP = packet addressing + routing across networks; 'end system
    host' = any IP-communicating device

- Moving data between IP networks requires an intermediate system =
    router

- ARP = resolves IP address → MAC address; bridges Internet layer to
    Link layer

- IP = 'best-effort' delivery: unreliable, connectionless —
    lost/out-of-order/duplicated/delayed packets possible

### 6.2.4 — Transport Layer

- Manages multiple simultaneous connections per host, across different
    Application layer protocols

- TCP: connection-oriented, reliable, recovers lost/out-of-order
    packets; used by most apps

- UDP: connectionless, unreliable, faster/lower overhead; used for
    time-sensitive apps (speech/video)

### 6.2.5 — Application Layer

- High-level functions (web, email, host management) — not
    addressing/transport

- Each app protocol uses a TCP or UDP port for client-server
    connections

- TCP/IP origin: US Dept of Defense → open standard; governance: IETF
    → RFCs (rfc-editor.org)

### 6.2.6 — IPv4 Addressing

- IP packet header's most important fields: source IP + destination
    IP

- IPv4 = 32 bits, 4 octets (8 bits each); dotted decimal = each octet
    converted to decimal

- Octet range: 0-255 → full range 0.0.0.0-255.255.255.255

- netsh interface ip set address = configure static IP; netsh
    interface ip set/add dns = configure DNS servers

### 6.2.8 — Network Prefixes

- IPv4 encodes Network ID (shared) + Host ID (unique per host)

- Prefix = contiguous 1-bits; /24 ↔ 255.255.255.0 (same value,
    different formats)

- Mask bit 1 = Network ID portion; mask bit 0 = Host ID portion

- Slash notation = refers to the network itself; mask notation = used
    for host configs

### 6.2.9 — IPv4 Forwarding

- Host compares masked source/destination — match = same network
    (deliver locally via ARP); no match = route via default gateway

- Default gateway must be in the same IP network as the host

### 6.2.10 — Public and Private Addressing

- Private ranges (RFC 1918): 10.0.0.0-10.255.255.255 (A),
    172.16.0.0-172.31.255.255 (B), 192.168.0.0-192.168.255.255 (C)

- Class A: 0-127, /8, 255.0.0.0; Class B: 128-191, /16, 255.255.0.0;
    Class C: 192-223, /24, 255.255.255.0

- Class D (224-239) = multicast; Class E (240-255) =
    experimental/future use

- Private hosts reach the Internet via: NAT (router translates) or a
    Proxy server

### 6.2.11 — IPv4 Host Address Configuration

- Minimum config = IP + subnet mask; full functionality needs
    gateway + DNS too

- First address in a network = network ID; last address = broadcast;
    valid hosts = everything in between

- Default gateway = router's IP; without it, host is local-only

- Primary DNS often = gateway address; preferred + alternate DNS =
    redundancy

### 6.2.12 — Static Versus Dynamic Host Address Configuration

- Static = manual, error-prone, doesn't scale — but needed for
    fixed-IP devices (routers, servers)

- DHCP = auto-assigns IP/mask/gateway/DNS; includes address pool +
    lease time

- APIPA = DHCP failover; self-assigned 169.254.0.1-169.254.255.254
    ('link local' outside Microsoft terms)

- APIPA hosts can only talk to each other on the same network, not
    route elsewhere

### 6.2.14 — SOHO Router Configuration

- Router has multiple interfaces (public WAN + private LAN), each
    needs own IP + subnet mask

- LAN interface IP = default gateway for hosts + router's management
    interface address

- 203.0.113.1 = NOT a real public address — reserved for
    documentation/examples

- Setup: connect via RJ45/default Wi-Fi → auto-obtain IP → browse to
    management URL → login with default creds → change password (12+
    chars) → wizard-based Internet setup

- Line status shows: upstream/downstream rates, SNR margin, line
    attenuation, error counts

### 6.2.15 — IPv6 Addressing

- IPv6 = 128-bit; hex notation, 8 groups of 16 bits; drop leading
    zeros, replace ONE zero-run with ::

- Structure: first 64 bits = Network ID, last 64 bits = Interface ID
    — no subnet mask needed

- Global address = Internet-unique, starts with 2 or 3; Link-local =
    local segment only, starts with fe80::

- SLAAC = auto-configures addresses via local router; no manual
    default gateway needed

- ND (Neighbor Discovery) = implements SLAAC, router discovery,
    ARP-equivalent function

- Dual stack = IPv4 + IPv6 simultaneously; IPv6 attempted first, falls
    back to IPv4

**6.2.16 Lesson Review — Key Takeaways (93%)**

- IPv6 subnet identification = the network ID (first 64 bits), NOT the
    interface ID

- IPv4 forwarding is a distinct router setting — can be disabled
    independently of correct addressing

- VPN = tool for secure remote access into a network

## 6.3 — Network Communications

### 6.3.1 — Protocols and Ports

- Transport layer identifies each application via a port number
    (0-65535)

- Multiple app traffic streams = multiplexed onto one link via port
    numbers

- Each conversation uses TWO ports: client's random source port +
    service's standard destination port; server flips these for replies

### 6.3.2 — Transmission Control Protocol

- TCP = connection-oriented; three-way handshake: SYN → SYN/ACK → ACK

- Sequence numbers track packets; ACK confirms receipt; NACK forces
    retransmission; FIN closes session

- TCP overhead: adds 20+ bytes per packet

- Must-use-TCP: HTTPS (encrypted web), SSH (encrypted remote CLI) —
    fail entirely if even one packet is lost

### 6.3.3 — Network Packets

- Large data → broken into smaller packets; each packet = data +
    header (sender, receiver, order)

- Packetization lets multiple devices share the network simultaneously

### 6.3.4 — User Datagram Protocol

- UDP = connectionless, no sequencing/acknowledgment, no delivery
    guarantee — trades reliability for speed

- DHCP uses UDP because it needs BROADCAST — TCP doesn't support
    broadcast at all

- TFTP uses UDP because it implements its own acknowledgment system at
    the Application layer

### 6.3.5 — Wireshark

- Packet sniffer/capture tool; shows overall traffic flow, packet
    headers, and content/payload

- Encrypted (TLS) traffic shows little/nothing readable; unencrypted
    traffic fully readable

- ⚠ Unencrypted protocols (plain FTP) can leak credentials in
    plaintext

- Fix = encrypted protocol versions: HTTPS, FTPS

### 6.3.6 — Well-Known Ports

- Ports assigned by IANA. 20/21=FTP; 22=SSH; 23=Telnet; 25=SMTP;
    53=DNS; 67/68=DHCP; 80=HTTP

- 110=POP; 137-139=NetBIOS; 143=IMAP; 389=LDAP; 443=HTTPS;
    445=SMB/CIFS; 3389=RDP

**6.3.7 Lesson Review — Key Takeaways (100%)**

- IMAP(143) keeps mail on server for multi-device sync; POP3(110)
    downloads and removes it

- Client packets reaching server but unanswered on expected port →
    server likely listening on a different port

- TCP handshake stalling after SYN/ACK, before final ACK → classic
    firewall-blocking symptom

## 6.4 — Network Configuration Concepts

### 6.4.1 — DHCP Functions

- DHCP scope = range of IPs offered; must exclude statically-assigned
    addresses

- DORA: Discover (broadcast) → Offer (server proposes) → Request
    (client confirms) → Acknowledge (server finalizes)

- DHCP = UDP; server port 67, client port 68

- After ACK, client ARPs to verify address isn't already in use

- DHCP reservation = server maps specific MAC addresses → specific IPs

### 6.4.2 — Domain Name System

- FQDN = host name + domain + suffix; format:
    host.subdomain.domain.TLD

- DNS = global hierarchy; Root (.) → 13 root servers (A-M) → TLDs
    (generic/sponsored/country code)

- ICANN operates DNS + manages generic TLDs

### 6.4.3 — DNS Queries

- Browser/client = 'stub resolver' — checks local cache first,
    then forwards to local DNS server

- DNS communication happens over port 53

### 6.4.4 — DNS Record Types

- A record = hostname→IPv4; AAAA record = hostname→IPv6

- CNAME = links one domain name to another (e.g., redirecting old
    company URL)

- MX record = identifies mail server(s); lower preference number =
    preferred; target hostname MUST have its own A/AAAA record

### 6.4.5 — DNS Spam Management Records

- TXT record = free-form text; commonly used for email spam/spoofing
    prevention

- SPF = ONE per domain, lists authorized sending hosts (-all=reject,
    ~all=flag, +all=accept)

- DKIM = public encryption key as TXT record; cryptographically
    validates sending server

- DMARC = ensures SPF/DKIM used effectively; specifies failure
    handling + reporting

### 6.4.6 — Virtual LANs

- Same unmanaged switch = same broadcast domain; large domains hurt
    performance at enterprise scale

- VLAN = managed switch feature, logically divides ports; VLAN ID
    range 2-4094; VLAN 1 = default

- Different VLANs can't communicate directly even on the same switch;
    each needs own subnet/DHCP/DNS

- Inter-VLAN communication requires an IP router

- Security benefit: VLANs = separate zones, inter-VLAN traffic
    filterable/monitorable

### 6.4.7 — Virtual Private Networks

- VPN = connects remote hosts to a LAN over the Internet via a remote
    access server

- VPN tunnel uses encryption + authentication; remote host effectively
    becomes part of the LAN

- Use cases: remote access (teleworkers), site-to-site (branch↔HQ), or
    internal security layer

- Data is encrypted AND encapsulated inside another packet —
    unreadable even if intercepted

**6.4.8 Lesson Review**

- (Review completed as part of module progression — see 6.7 Module
    Quiz for consolidated takeaways)

## 6.5 — Challenge Lab: Install a SOHO Network

- Full hands-on integration: connect router to WAN port, configure
    DHCP scope, connect PCs (auto-DHCP/DNS), connect and configure a
    wireless AP (separate management IP from the router), configure
    SSID/WPA2-PSK/AES, connect wireless clients

- ⚠ Watch for physical wireless on/off switches on older laptops — a
    hardware-level override that looks like a software connection
    problem

## 6.6 — Additional Resources

### 6.6.1 — Ports and Protocols (video recap)

- Port field = 16 bits wide → max value 65,535

- Well-known ports: 0-1023 (standardized); Registered ports:
    1024-49,151 (vendor-registered); Dynamic ports: 49,152-65,535
    (client's random source port)

- Source/destination ports SWAP between request and reply

- Upper-layer protocols = user-facing (HTTP, FTP, SSH);
    lower-layer/support = TCP/UDP/IP

### 6.6.2 — DHCP and DNS Services (video recap)

- DHCP Relay = router forwards DHCP requests to a separate DHCP server
    rather than serving them itself

- DHCP broadcast destination = all Fs (FF:FF:FF:FF:FF:FF)

- DHCP scope includes the DNS server address too, bundled into the
    same handoff

- Enterprise DNS servers resolve internal resources too (printers,
    FTP, mail), not just public websites

- PTR (Pointer) record = reverse DNS — IP → name; useful for
    security investigation

## 6.7 — Module Quiz — Key Takeaways (100%)

- NXDOMAIN DNS response = the domain itself doesn't exist/isn't
    registered — distinct from a DNS server being unreachable (timeout
    instead)
