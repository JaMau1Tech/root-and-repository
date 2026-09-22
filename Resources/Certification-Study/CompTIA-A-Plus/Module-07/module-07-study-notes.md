# Module 7 Study Notes

*Supporting Network Services — CompTIA A+ Core 1 (220-1201)*

Module 7 complete: Lessons 7.1-7.3, the 7.4 troubleshooting lab, all of
7.5's additional resources and exercises, the Module 7 Quiz, and the
7.7 cumulative checkpoint.

## 7.1 — Networked Host Services

### 7.1.1 — File/Print Servers

- File share = server's shared disk; client = machine accessing it;
    client/server architecture

- SMB = Windows file/print sharing protocol, TCP/445; SMB3 current,
    SMB1 disabled by default (vulnerable)

- Samba = lets Linux/NAS act as an SMB server; CIFS = technically just
    one old SMB1 dialect, used loosely as a synonym

- Print servers = centralize/queue print jobs; can hold a job until
    released (confidential printing)

- NetBIOS/NetBT = legacy pre-TCP/IP naming; UDP/137 (names), UDP/138
    (connections), TCP/139 (sessions) — obsolete, disable unless
    supporting pre-Windows 2000

- FTP = TCP/21 (control) + TCP/20 active or server-assigned port
    passive (data)

- ⚠ Plain FTP = unencrypted, plaintext passwords → use FTPS or SFTP

### 7.1.2 — Database Servers

- Database server = stores/organizes/manages large structured or
    unstructured data, far beyond flat-file capability

- Relational/SQL: tables (rows/columns), linked by relationships,
    queried with SQL — Oracle, MySQL, MariaDB

- Non-relational: graphs/documents/key-value pairs, flexible
    structure, scales for large varied data — MongoDB, CouchDB, Amazon
    SimpleDB

### 7.1.3 — Web Servers

- Web server = HTTP/HTTPS access; client connects on TCP/80 by
    default, sends GET

- POST = client submits data to server (forms, etc.); HTML = tagged
    plain text the browser renders

- URL = Protocol + FQDN/host (not case-sensitive) + File path (may be
    case-sensitive)

- IPv6 addresses in a URL must be in square brackets

- Web deployment: ISP-leased, self-hosted, or internal; Intranet =
    local-only, Extranet = permits remote access

### 7.1.4 — Hypertext Transfer Protocol Secure

- HTTP = no encryption, no authentication; SSL (Netscape) → TLS (IETF
    standard) fixed this

- HTTPS = HTTP + TLS, TCP/443; 'S' suffix on any protocol name =
    TLS/SSL securing it

- DTLS = TLS over UDP, common in VPNs

- HTTPS requires: CA-issued digital certificate, public/private key
    pair (private key secret on server, public key shared via cert)

- Public key can be freely known; only the private key can decrypt —
    keeps the tunnel secure

- Padlock icon + https:// = trusted, encrypted session; sites can
    force HTTPS-only

### 7.1.5 — Mail Servers

- Email address = username@domain (mailto scheme)

- SMTP = server-to-server AND client-submission delivery; looks up
    recipient via DNS MX record

- TCP/25 = server-to-server relay (MTA), usually insecure; TCP/587 =
    client submission (MSA), should be encrypted/authenticated

- POP3 = TCP/110 (or 995 secure) — downloads mail, typically deletes
    from server after

- IMAP = TCP/143 (or 993 secure) — keeps mail ON server, supports
    permanent/multi-client connections, folder management

- Full path: client→local SMTP(587)/IMAP(993 Sent) → local SMTP finds
    remote via MX → remote SMTP(25) → remote IMAP Inbox → recipient's
    client via IMAP(993)

**7.1.7 — Navigate a Mailbox Server (video)**

- Email client = middleman between user and mail server; auto-config
    often fails → manual setup needed

- Manual setup needs: account type, incoming server, SMTP server,
    credentials

- Advanced tab = where port + encryption type get specified — always
    sourced from the email provider

### 7.1.8 — Directory and Authentication Servers

- Directory server = centralized user account database; enables SSO

- LDAP = queries/updates an X.500-style directory (AD, OpenLDAP);
    TCP/UDP 389, LDAPS = TCP/636

- AAA consolidates authentication across many access devices instead
    of storing creds on each

- Supplicant = device requesting access; NAS/NAP = access appliance,
    relays only, never stores credentials; AAA server = actual auth
    server

- RADIUS = TCP/UDP 1812/1813, authenticates USERS; TACACS+ = TCP/49,
    authenticates DEVICES (routers/switches)

### 7.1.9 — Remote Terminal Access Servers

- Terminal emulator = software replicating old TTY input/output
    function

- SSH = secure CLI access, TCP/22; also enables SFTP; OpenSSH most
    common implementation

- Telnet = unencrypted CLI access, TCP/23; passwords/traffic sniffable
    — replaced by SSH

- RDP = Microsoft's GUI remote access protocol, TCP/3389;
    cross-platform clients exist; xrdp = open-source server option

### 7.1.10 — Time Servers

- NTP = syncs clocks across a network; UDP/123

- Stratum-0 = atomic clock; Stratum-1 = synced directly to Stratum-0;
    Stratum-2 = synced to a Stratum-1 server

- Windows default time source = time.windows.com; check via w32tm
    /query /status

- NTS (2020) = TLS-secured time sync, TCP/4460

### 7.1.11 — Network Monitoring Servers

- SNMP: Agent (device-side, maintains MIB stats) + Management system
    (polls agents) + Trap (proactive alert)

- SNMP queries = UDP/161; traps = UDP/162; SNMPv1/v2 insecure, avoid;
    SNMPv3 preferred (authentication)

- Syslog = log aggregation standard; collector = UDP/514

- Syslog message = PRI code (facility+severity) + header
    (timestamp/hostname) + message (source process + content)

**7.1.12 Lesson Review — Key Takeaways (93%)**

- Missed: AAA — Supplicant = device REQUESTING access; NAS/NAP = the
    relay that does NOT store credentials (these two are easy to mix up)

- Server-role questions repeatedly test matching function to name:
    file/print, database, web, mail, directory/auth, monitoring —
    don't mix them up

- Telnet vs SSH: Telnet = zero security features (plaintext
    everything); don't attribute SSH's encryption to Telnet

- LDAP port (389) vs RDP port (3389) — visually similar, easy to
    misread

## 7.2 — Internet and Embedded Appliances

### 7.2.1 — Proxy Servers

- SOHO routers use PAT (overloaded NAT) — one public IP, unique
    ports per device

- Proxy server ≠ simple NAT — inspects the ENTIRE request and reply,
    not just addresses; works for HTTP and other protocols

- Transparent proxy = no client config needed; Non-transparent =
    client manually configured with proxy IP + port (commonly 8080)

- Proxy security functions: content filtering, time-based access
    rules, caching (performance + bandwidth savings)

### 7.2.3 — Spam Gateways and Unified Threat Management

- Firewall = ACL-based allow/block; IDS = detects + alerts only; IPS =
    detects + actively blocks

- Antivirus/anti-malware = scans files for known signatures

- Spam gateway = SPF/DKIM/DMARC-based mail authenticity verification +
    filtering, before inbox delivery

- Content filter = blocks outgoing access to unauthorized sites; DLP =
    scans outgoing traffic for confidential data

- UTM = combines multiple security functions into one centrally
    managed appliance

- Signature-based detection = matches known attack patterns;
    Heuristic/behavior-based = baselines normal activity, flags
    deviations (more false positives)

- Defense in depth = use IDS + IPS together; IDS logs remain valuable
    even when IPS blocks the live threat

### 7.2.4 — Load Balancers

- Load balancer = distributes requests across a pool of
    identical-function servers (web, email, streaming)

- Presents one virtual server address to clients

- Enables high availability + scaling from light to heavy load

- Persistence mechanism = keeps a client tied to the same backend
    server across a session

### 7.2.5 — Legacy Systems

- Legacy system = no longer vendor-supported (EOL); kept because
    replacement is too costly/complex

- Works fine functionally — exactly why it's not replaced — but
    NO future security patches possible

- Mitigation = isolate from the rest of the network, monitor/protect
    any remaining network links carefully

### 7.2.6 — Embedded Systems and SCADA

- Embedded system = dedicated-function device, traditionally on a
    closed network

- ICS = workflow/process automation for critical infrastructure
    (power, water, healthcare, telecom)

- ICS components: PLCs (embedded controllers) + actuators (do physical
    work) + sensors + HMI (human interface) + control server + data
    historian (logs everything)

- Embedded system network = OT (Operational Technology), distinct from
    IT network

- SCADA = replaces control server for LARGE-SCALE, MULTI-SITE ICS;
    manages 'field devices' over WAN (cellular/satellite) — NOT
    local Wi-Fi/LAN/USB

### 7.2.7 — Internet of Things Devices

- IoT = network of everyday objects with sensors/software/connectivity

- Hub/control system = wireless networking backbone + control (needed
    since many IoT devices are headless)

- Smart device = the actual endpoint (bulb, thermostat, doorbell);
    usually Linux/Android-based, vulnerable to standard web/network
    attacks

- Smart devices often use Z-Wave or Zigbee (low-power protocols) to
    reach the hub, separate from hub's own Wi-Fi

- Internet-enabled device = remotely controllable, doesn't decide/act
    on its own (smart bulb)

- True IoT device = gathers data AND acts/communicates automatically,
    minimal human input (smart thermostat)

**7.2.8 Lesson Review — Key Takeaways (90%)**

- Missed: SCADA field devices communicate via WAN (cellular/satellite)
    — NOT Wi-Fi. Wi-Fi is still local-range; SCADA's whole point is
    multi-site/long-distance

- Test-taking cue: when a question emphasizes 'multiple sites' or
    'large-scale,' think WAN-class technology, not local wireless

- UTM = correct answer whenever a scenario lists MULTIPLE distinct
    security needs on a budget (vs. picking one single-function device)

- Proxy server's specific signature = caching + full request/reply
    inspection, not just NAT-style translation

## 7.3 — Troubleshoot Networks

### 7.3.1 — Troubleshoot Wired Connectivity

- Full chain: NIC → patch cord → wall port → structured cable (IDC) →
    patch panel → patch cord → switch port → transceiver

- Link LEDs = active/speed indicator; flicker = activity

- Troubleshoot order: patch cords (swap/test) → transceivers (loopback
    tool or host/port swap) → structured cabling (cable
    tester/certifier) → speed/duplex config (auto-negotiate) + NIC
    driver update

- Port flapping = interface cycling up/down — usually bad cable,
    interference, or faulty NIC

### 7.3.2 — Troubleshoot Network Speed Issues

- Mismatched duplex = reduced speed; Gigabit should be auto-negotiate
    both ends

- Structured process: identify specific slow activity → measure actual
    transfer rate (app-independent) → check interference if isolated to
    one segment → check crosstalk (bad termination) via tap/analyzer or
    switch error rates → shielded cable if needed → check/update NIC
    driver → rule out malware → establish scope (single
    user/switch/network-wide)

**7.3.3 — Lab: Fix a Network Connection**

- No DHCP server on this network → static IP required on affected host

- Reserved ranges given: below .15 = servers, .30-.34 = other
    workstations — pick an address outside both ranges

- Confirm subnet mask matches network default; confirm gateway/DNS
    fields point to correct server addresses

- Problem may be OS config AND/OR hardware — check both, and check
    for more than one issue

- Success = ping Office2 AND ping the DNS server

### 7.3.4 — Troubleshoot Wireless Issues

- Weak/intermittent signal → try moving devices closer first

- Auth failure = wrong password or wrong security standard

- SSID not found = out of range OR hidden SSID (needs manual config)

- Legacy 802.11b clients force AP into higher-overhead compatibility
    mode — upgrade old devices rather than let them join

- Some 802.11n clients are 2.4GHz-only — check radio capability if
    5GHz fails

- RSSI too low → speed steps down or connection drops/flaps between
    weak networks

- Interference sources: same-frequency networks (change channel),
    motors/microwaves (EMI), physical obstructions (metal, foil-backed
    drywall, concrete, mirrors)

- Wi-Fi analyzer: dBm closer to 0 = stronger signal; shows channel
    congestion — move to less congested channel

- Enterprise roaming drops = check AP config + confirm client supports
    roaming

### 7.3.5 — Troubleshoot VoIP Issues

- Bursty data (HTTP/FTP/email) = tolerates delay, sensitive to loss;
    Real-time (VoIP/video) = opposite

- Latency = one-way signal time (ms); VoIP max ≈150ms one-way; RTT =
    round-trip time

- Jitter = variation in delay over time; VoIP tolerates ≈30ms via
    buffering; caused by router/switch congestion

- QoS = prioritizes VoIP traffic over bursty data; hard to guarantee
    over the public Internet

- SOHO routers may have a Bandwidth Control feature = basic QoS for a
    specific port/app

- Persistent high latency beyond agreed service level → escalate to
    ISP

### 7.3.6 — Troubleshoot Limited Connectivity

- 'Limited connectivity' (Windows) = physical link OK, but no DHCP
    lease → APIPA (169.254.x.y)

- Multiple users affected = likely the DHCP server itself; leases take
    time to expire, symptoms appear gradually

- Check patch cord/wall port → correct switch port mapping first

- Wrong VLAN ID on a switch port = same symptom as wrong port entirely

- 'No Internet access' (adapter HAS an IP) = gateway/Internet
    problem OR DNS resolution failure — check router status, contact
    ISP if link down, verify DNS reachability

**7.3.7 Lesson Review — Key Takeaways (93%)**

- Missed: network-wide slowdown (ALL users affected) → check for
    congestion at shared infrastructure (switch/router), NOT individual
    host hardware

- Core principle reinforced across the whole lesson: scope tells you
    where to look — one user = check that host; one switch = check
    that switch; whole network = check shared infrastructure

**7.4 — Lab: Troubleshoot a Network Issue**

- Issue Trax ticket: laptop can't connect to CorpNet wireless

- Root cause found: physical Wi-Fi hardware switch on the laptop was
    toggled off — looked like a software/config issue but was a
    hardware toggle

- Reinforces 'question the obvious' (Module 1) — check simple
    physical explanations (switches, cables, power) before
    troubleshooting configuration

## 7.5 — Additional Resources

### 7.5.1 — Client-Server Relationship (video recap)

- Server = provides a service; Client = requests/uses it; one server
    machine can run multiple services at once

- Restaurant analogy: server=waiter, service=what's provided,
    client=customer

- Reframes 7.1's server roles in plain language: web
    server=request/response, file server=centralized storage, mail
    server=storage+routing, print server=shared queue

- Core benefits of client-server model: efficiency, shared resources,
    centralized administration/security

### 7.5.2 — Troubleshooting Networks (field interview)

- Physical checks always first: cable plugged in, visible damage, link
    lights active

- Poor cable management = root cause of many connectivity issues +
    makes troubleshooting harder — label and organize cabling
    proactively

- 'Has this ever worked before?' — never worked = configuration
    issue; used to work = something changed (echoes Module 1's 'what
    changed?' question)

- Wireless troubleshooting should account for environmental CHANGES
    over time (new furniture, renovated walls), not just static building
    materials

- Keep in-progress notes DURING troubleshooting, not just the final
    ticket comment — avoids repeating already-ruled-out steps

**7.5.3 — Exercise: Server Comparison Project (File Server vs.
Database Server)**

- File server: centralized shared storage; SMB/NFS; large storage
    capacity emphasis; limitation = not designed for structured querying

- Database server: structured/unstructured data storage + querying;
    SQL or non-relational engines; CPU/RAM emphasis; limitation = more
    complex to set up/maintain

**7.5.4 — Exercise: Exploring Everyday Embedded Systems (Fitness
Tracker)**

- Embedded system = dedicated microcontroller + sensor array
    (accelerometer, heart-rate sensor) doing one job continuously

- Low-power design (BLE) enables multi-day battery life vs. constant
    connectivity

- True IoT distinction: on-device activity classification (walking vs
    running) = autonomous decision-making, not just remote control

**7.5.5 — Exercise: Troubleshooting with Command-Line Tools**

- ipconfig/ifconfig = verify IP config (APIPA/missing gateway = DHCP
    failure)

- nslookup = test DNS resolution; successful resolution RULES OUT DNS,
    points elsewhere (server down, firewall, routing)

- netstat = view active connections; many repeated connections to
    unfamiliar IPs on unusual ports = possible malware/C2 traffic

- arp -a = view IP-to-MAC mappings; 'incomplete' entry = device not
    responding at that IP (offline, address changed, or physical issue)

- ping = test connectivity/latency/packet loss; loss specifically to
    the DEFAULT GATEWAY = local physical-layer problem, not something
    further out

**7.5.6 — Exercise: Build a Smart Home Device Capstone
(Motion-Activated Light)**

- Embedded system = Raspberry Pi Pico (microcontroller) + PIR sensor
    (input) + LED (actuator) — full sense→decide→act loop

- Wokwi = free browser simulator for microcontrollers (Pico, Arduino,
    ESP32) — cannot simulate a full Linux-based Raspberry Pi 3/4/Zero

- Design logic: track last-motion timestamp, compare elapsed time
    against a timeout constant, turn actuator off only once timeout is
    exceeded

- Real-world tuning example: adjusting timeout duration (10s→15s)
    based on expected room use case

Module 7 Quiz — Key Takeaways (100%)

- UTM's core advantage = consolidating
    configuration/monitoring/reporting to one dashboard + enabling
    functions not otherwise available together — NOT the same as any
    one individual function (spam gateway, proxy) it might include

- RBAC (Role-Based Access Control) = practical mechanism implementing
    'Authorization' in AAA — assigns permissions by role, not
    per-user

- Damaged frame counts (analyzer/switch reporting) = the specific tell
    for EXTERNAL INTERFERENCE — distinct symptom from duplex mismatch,
    bad termination, or outdated drivers

- Scope + symptom together narrow the cause: single user + physical
    layer already ruled out → check that host's software; multiple
    users/one switch + damaged frames → shared cabling/interference

- Self-hosting in an owned datacenter = maximizes control (vs.
    leased/cloud/shared hosting, which trade control for
    cost/convenience) — right answer whenever a scenario prioritizes
    security/control above all else

- IoT = right technology for
    smart-home/accessibility/independent-living scenarios; SCADA is
    industrial-only, wrong context for residential use

- Before troubleshooting 'everyone on this device is slow,' first
    confirm whether the shared device is a HUB or a SWITCH — changes
    what the symptom even means (hub = shared bandwidth, switch =
    dedicated per-port)

## 7.7 — Checkpoint Quiz (Cumulative Review, Modules 1--7)

This checkpoint pulled from across the entire course to date, not just
Module 7 — a genuine cumulative review. Key answers and reasoning
below.

- Old PC, no USB, keyboard/mouse connector = DB9 (legacy serial,
    Module 2)

- NIC tested and works fine → theory disproven → establish a NEW
    theory (1.2.5)

- Confirmed RAM shortage → plan of action = install additional RAM per
    manufacturer's guide

- US→UK relocation, PSU voltage mismatch → check for a manual 115/230V
    switch on the PSU; modern auto-switching PSUs need no action

- ISP needs rural coverage + minimal interference → Licensed
    long-range fixed wireless (exclusive spectrum rights)

- Grinding/clicking diagnostic = HDD only (mechanical, moving parts)

- Streaming video, glitches but no crash → UDP (tolerates loss as a
    glitch, not a failure)

- Optical storage devices = CD, DVD, BD (NOT HDD/SSD/USB flash/SDHC
    — those are magnetic or flash media)

- Windows limited connectivity, first check = patch cords (physical
    layer before DHCP scope/congestion)

- RS-232's real modern limitation = requires specialized/incompatible
    cables and adapters — NOT high-speed (it's slow) and NOT
    primarily video

- Flat panel monitor, several black dots (dead pixels) = check for
    warranty replacement (generally not repairable)

- Two new HDDs, only one drive letter shows → check Windows Disk
    Management FIRST (likely just needs initializing/formatting, not a
    hardware fault)

- PCI card keying misaligned on an old system → a 3.3V card was
    inserted in a 5V slot (older boards often only support 5V PCI)

- New USB device, unfamiliar error → check manufacturer's website
    FIRST, before uninstalling/replacing hardware

- Motherboard form factor best for low-power PSUs = Mini-ITX (smallest
    standard form factor)

- Scheduled an HDD upgrade repair, components identified — forgotten
    step = perform a backup BEFORE the repair

- Down-plugging (longer card, shorter slot) = PCIe-specific behavior

- Benefit of good documentation = saves time/money in future
    troubleshooting (not elimination of troubleshooting itself)

- Common cause of reduced cabled link speed = mismatched duplex
    settings on NIC/switch port

- Dim display troubleshooting = check brightness/contrast, check
    adaptive brightness settings, check for failing backlight — NOT
    burn-in (that's a ghost-image symptom, unrelated to overall
    dimness)

- Blank screen at power-on troubleshooting = check internal cabling +
    check for faulty interfaces — NOT changing system time or reading
    a BSOD (no display = can't do either)

- Quad-channel memory underperforming, additional checks = mismatched
    modules, flex mode, full complement installed (3.3.5)

- Fault tolerance against data loss = RAID (mirroring/parity) — not
    SSD/NVMe/mSATA, which are just drive types

- VLAN performance/security benefit = reduces broadcast domain size,
    isolates traffic between groups

- NEW (Module 9 preview): mobile device touch input component = the
    Digitizer — a separate layer from the display itself that senses
    touch and converts it to digital input

- LAN cabling primarily = copper twisted pair (UTP) — fiber is more
    common for backbones, coax for cable internet, satellite for
    WAN/internet access
