# Module 5 Study Notes

*Comparing Local Networking Hardware — CompTIA A+ Core 1 (220-1201)*

## 5.1 — Network Types

### 5.1.1 — LANs and WANs

LAN = computers connected via cabling + switches, all at a single site
(~1-2km range). Org-owned/managed.

- Ethernet naming: xBASE-Y; 100BASE-T=100Mbps, 1000BASE-T=1Gbps
    (mainstream), 10GBASE-T=10Gbps

- Most LANs = copper (electrical); backbone/specialized segments often
    = fiber (light)

- WAN = multiple sites; Internet = biggest example; ISP = provides WAN
    access

- WLAN = IEEE 802.11 = Wi-Fi; complements Ethernet, often same LAN

- MAN = city-sized, bigger than LAN, smaller than WAN

- PAN = few-meter wireless range; wearables/peripherals; e.g.
    Bluetooth earbuds+smartwatch to phone

- SAN = dedicated storage-only network; block-level access;
    consolidated storage; high-speed (Fibre Channel/iSCSI)

### 5.1.2 — SOHO and Enterprise Networks

- SOHO = small network, single all-in-one router (routing +
    switching + Wi-Fi + modem)

- Enterprise = same functions, split into separate dedicated devices
    — each segment = modular function

- Enterprise flow: Work Area → Wall Ports → Patch Panel → Workgroup
    Switches → Core/Distribution → Servers/DMZ/VPN/ISP

- DMZ = screened subnet, buffer between private LAN and public
    Internet; heavily filtered/monitored

### 5.1.3 — Datacenters

- Server = hosts apps/resources; Client = end-user access point

- Enterprise LAN = servers isolated in a server room

- Datacenter = whole dedicated site for server provisioning; dedicated
    networking, power, climate control, physical access control

### 5.1.4 — SOHO/Enterprise/PAN (Scale Analogies)

- PAN = personal bubble; SOHO = neighborhood; Enterprise = city road
    network

- Network type should match actual scale of need

**5.1.5 Lesson Review — Key Takeaways (100%)**

- Enterprise/private WANs = leased ISP equipment, not
    Bluetooth/wireless-only

- Common PAN tech = Bluetooth

- Router = forwards BETWEEN networks; Switch = connects WITHIN a
    network; AP = wireless hosts; NIC = signal conversion

- MAN = best fit for multi-location company within one city

- Datacenter high-availability feature = climate control

## 5.2 — Networking Hardware

### 5.2.1 — Network Interface Cards

NIC = physical connection point (transceiver port) for Ethernet; most
motherboards have built-in 1000BASE-T.

- Multiple NIC ports can be bonded → combined higher-speed link

- Ethernet's data link protocol = handles framing + addressing

- MAC address = unique hardware address per NIC port; in every
    frame's header (source + destination)

- MAC = 48 bits = 6 bytes = 12 hex digits (e.g., 00:60:8C:12:3A:BC)

- MAC structure: first 24 bits = OUI (manufacturer); last 24 bits =
    NIC-specific unique ID

- Flag bits (1st hex pair, in binary): last bit =
    individual(0)/multicast(1); next bit = universal(0)/locally
    administered(1)

- Broadcast address = special destination MAC meaning 'send to all
    nodes'

### 5.2.3 — Patch Panels

- Cabling flow: computer → wall port → in-wall cabling → patch panel
    (rear: IDC punchdown blocks)

- Patch panel front = pre-wired RJ45 ports; patch cord connects panel
    port → switch port

- Design benefit: reconfiguring = move a patch cord, no need to touch
    in-wall cabling

- ⚠ Labeling system essential — track which patch panel port maps to
    which wall port

### 5.2.4 — Wiring a Patch Panel (Practical Walkthrough)

- Workflow: activate patch panel port (→ switch) → connect computer to
    wall port (CAT6) → configure IP (static→DHCP) → verify

- 'Activating a drop' = connecting patch panel side to a switch port

- Switch port numbering/orientation indicators matter for correct
    physical port ID

**5.2.5 Lab — Connect Patch Panel Cables**

- Applied the patch panel + wall port + DHCP configuration workflow
    from 5.2.3/5.2.4 in a hands-on lab

### 5.2.6 — Switches

Switch connects multiple devices, provisioning one port per device.
Learns MAC addresses passively from incoming traffic.

- MAC address table = maps MAC address → switch port

- Forwarding: read destination MAC → look up table → send only to
    matching port (not broadcast)

- Unknown destination MAC → switch floods frame out ALL ports (except
    source)

- Each switch port = separate collision domain → collisions eliminated

- Full duplex = simultaneous independent send + receive at full
    cable/NIC speed

### 5.2.7 — How Does an Access Switch Forward Data?

- MAC address = unique device identifier, like a house address

- MAC table built dynamically from observed traffic, not
    pre-configured

- Complete table = switch forwards directly, no flooding needed

**5.2.8 Lab — Connect Computers with a Switch**

- Built a SOHO topology in a network modeler: computers → switch →
    router

### 5.2.9 — Unmanaged and Managed Switches

- Unmanaged: zero config, plug-and-play, typically 4-8 ports, common
    in SOHO router/modems

- Managed: works unmanaged out-of-the-box, but configurable via
    management port; typically 24-48 ports, rack-mounted

- Uplink ports = connect switches to other switches for scaling

- Modular switches = shared power supply + backplane interconnecting
    multiple switch units → hundreds of ports from one chassis

- Managed switch config: web interface or CLI

### 5.2.10 — Power over Ethernet

- PoE = power + data over same Ethernet cable, no separate power cable

- 802.3af (Type 1) = ~13W usable (basic VoIP/AP/camera)

- 802.3at (PoE+/Type 2) = ~25W, 600mA max (advanced AP, PTZ camera,
    video IP phone)

- 802.3bt (PoE++/Type 3-4) = ~51-73W (LED lighting, signage, POS
    systems)

- Usable power always less than spec due to voltage drop over max 100m
    cable

- PoE switch = 'endspan PSE'; detects PoE-capability before
    supplying power

- PoE injector ('midspan') = adds PoE capability when switch
    doesn't support it; still capped at 100m

**5.2.11 Lesson Review — Key Takeaways (100%)**

- Modular switches = interconnect multiple units via fast backplane

- PoE injector = enables PoE when switch itself doesn't support it

- Switches/bridges learn from SOURCE MAC only — never destination

- Switches operate at Layer 2 — no IP address involvement

- Patch panel also protects switch ports from wear — patch cables
    absorb reconnection wear

- 802.1X (auth) and 802.11n (Wi-Fi) are NOT PoE standards

- PoE tiers: 802.3af ≈13W, 802.3at ≈25W, 802.3bt Type 3/4 ≈51W/73W

## 5.3 — Network Cable Types

### 5.3.1 — Unshielded Twisted Pair

- UTP = most popular network cable, copper, 4 twisted wire pairs (8
    wires total)

- Different twist rate per pair = reduces interference

- Balanced signaling = each wire in a pair carries equal/opposite
    signal, aids interference resistance

- Signal suffers attenuation (weakens over distance); max recommended
    distance: 100m (328 ft)

### 5.3.2 — Shielded Twisted Pair

- STP = generic term for shielded cable; used where high external
    interference exists (fluorescent lighting, power lines, motors,
    generators)

- F/UTP (ScTP/FTP): single outer foil shield — decent protection,
    reasonable cost

- S/FTP (or F/FTP): braided/foil outer shield + individually shielded
    pairs — best protection, expensive/less flexible

- U/FTP: no outer shield, individually shielded pairs only — good
    protection

- ⚠ Shielding MUST be bonded to the connector — unbonded shielding
    can act as an antenna and generate interference

### 5.3.4 — Cat Standards

- Cat spec defined by TIA/EIA-568-C; printed on cable jacket

- Cat 5 = 100 Mbps, obsolete; Cat 5e = 1 Gbps, still viable

- Cat 6 = 1 Gbps @ 100m OR 10 Gbps @ reduced 55m

- Cat 6A = 10 Gbps @ full 100m; recommended for healthcare, PoE
    802.3bt, AP distribution cabling

- Cat 7 = 10 Gbps @ 100m or 100 Gbps @ 15m; connectors = GG45/TERA
    (RJ45 can't deliver full spec)

- Cat 8 = 25 Gbps or 40 Gbps @ 30m; Cat 8.1 = RJ45 (backward
    compatible); Cat 8.2 = GG45/TERA (NOT backward compatible)

- Cat 7/8 mainly used in data centers — not typical home/office
    deployment yet

### 5.3.5 — Copper Cabling Connectors

- RJ45 = '8P8C' (8-Position/8-Contact)

- 4 color pairs: orange, green, blue, brown — one striped/white
    conductor + one solid conductor per pair

- T568A: pin1=green/white, pin2=green, pin3=orange/white, pin6=orange

- T568B: orange and green pair positions swapped (orange→1,2;
    green→3,6)

- Straight-through cable = same standard both ends; Crossover cable =
    T568A one end, T568B the other

- RJ11 = terminates 2-pair cable (not 4-pair like Ethernet) —
    telephone/DSL, not Ethernet

**5.3.6 Activity — Identify Copper Connectors**

- BNC = twist-lock, coaxial; RJ45 = wide clear plastic, 8 pins,
    Ethernet

- F-Type = threaded screw-on, coaxial (CATV); RJ11 = narrower plastic,
    phone/DSL

### 5.3.7 — Copper Cabling Installation Tools

Structured cabling: computer → patch cord → wall port → permanent cable
→ patch panel → patch cord → switch.

- Patch cords = RJ45 crimped plugs; Permanent cable = IDC/punchdown
    termination

- 100m limit = whole channel link, not just permanent cable; patch
    cords individually capped at 5m

- Permanent cable = solid core, rigid; Patch cords = stranded,
    flexible but more attenuation

- Cable stripper: scores outer jacket without damaging inner wire
    insulation

- Cat 6/6A have a plastic star filler — snip off before terminating

- Punchdown tool: presses wires into IDC terminals; blades cut
    insulation for contact; max ½" (13mm) untwisted per pair

- Crimper: attaches RJ45 plug to patch cord; tab latch faces down, pin
    1 = leftmost

### 5.3.8 — Copper Cabling Test Tools

- Test cable immediately after termination — errors easier to fix
    while you still have access

- Cable tester: pair of devices, one per end; energizes each wire, LED
    confirms termination

- No LED = damaged insulation or improperly seated wire; mismatched
    LED sequence = wires terminated to different pins each end

- Toner probe: traces one cable in a bundle via continuous audio
    tone + probe; disconnect far end from equipment first

- Loopback plug: tests NIC/switch/serial/parallel port directly; DIY =
    pin1↔pin3, pin2↔pin6; solid link LED = pass

- DIY loopback plugs don't work on Gigabit ports — need
    manufactured Gigabit-specific tester

### 5.3.9 — Network Taps

- Network tap = intercepts cable signal, sends to packet/protocol
    analyzer

- Passive TAP: inductor/optical splitter physically copies signal; no
    logic, no power; captures every frame; unaffected by load

- Active TAP: powered, performs signal regeneration; needed for
    Gigabit copper or certain fiber types

- ⚠ Active TAP = becomes a point of failure for the link if it loses
    power

- SPAN/mirror port = switch-based alternative — configured switch
    port receives copies of frames from nominated/all ports

### 5.3.10 — Copper Cabling Installation Considerations

- Cable installation must comply with local building/fire codes

- Plenum space = HVAC void (false ceiling/raised floor); fire-spread
    risk → requires fire-retardant plenum cable

- Plenum cable: no heavy smoke, self-extinguishing; General cable =
    PVC; Plenum = treated PVC/FEP — same bandwidth, less flexible

- NEC marking: CMP = plenum-rated; CMG/CM = general-purpose

- OSP (Outside Plant) = cable exposed outdoors; Aerial (UV/temp/damp
    degrade PVC), Conduit (still needs non-PVC), Direct burial (laid in
    earth/concrete, may need rodent armoring)

### 5.3.11 — Optical Cabling

- Fiber = light pulses, immune to interference, minimal attenuation →
    higher bandwidth, longer distances (miles vs feet)

- Structure: core (glass, carries light) → cladding (guides light) →
    buffer (protective coating) → jacket → connector

- Single-mode (SMF): small core (8-10 microns), long wavelength, laser
    diode, 10Gbps+, many km — WAN use

- Multimode (MMF): larger core (50/62.5 microns), short wavelength,
    LED/VCSEL, cheaper, shorter range — LAN use

- Connector core = ceramic/plastic ferrule for alignment

- ST = bayonet twist-lock, older MMF; SC = push/pull, simplex/duplex,
    SM or MM; LC = small form factor, higher port density

- MPO (Multi-Fiber Push-On) = push-on connector terminating multiple
    fiber strands at once (12/24); high-density data center/backbone use

- ⚠ Fiber connectors are fragile — avoid repeated plug/unplug; use
    dust caps on unused ports

**5.3.12 Activity — Identify Fiber Optic Connectors**

- SC = blue push/pull; LC = small duplex tan/white; ST = metal bayonet
    twist-lock; MPO = green wide push-on, multi-fiber

### 5.3.13 — Coaxial Cabling

- Coax = copper, electrical signal, interference resistance via
    physical shielding (not balancing like twisted pair)

- Layers: core conductor → dielectric (plastic insulation) → wire mesh
    (shielding + ground)

- Modern uses: CCTV, CATV patch cable, broadband cable modems

- F-Type connector = screw-down, standard for CATV; BNC = bayonet
    twist-lock, video/radio/TV

**5.3.14 Lesson Review — Key Takeaways (100%)**

- Crosstalk = interference between two pairs WITHIN the same cable,
    strongest at 'near end' — caused by excessive untwisting during
    termination

- Loopback plugs also test serial and parallel ports, not just
    Ethernet/NIC

- Combined-constraint questions (e.g., plenum + Gigabit +
    twisted-pair) require checking every stated requirement, not just
    the first match

- T568A pin 1 = green with white

## 5.4 — Wireless Networking Types

### 5.4.1 — Access Points

- Wireless = radio waves; antennas tuned to specific frequencies;
    WLANs = IEEE 802.11 = Wi-Fi

- Infrastructure mode = clients (stations) connect via an AP, not
    directly to each other

- BSS = infrastructure Basic Service Set; BSSID = MAC address of the
    AP's radio

- AP can be wireless-only, or bridge to a wired network (the
    'distribution system'/DS)

- AP components: Ethernet port (uplink to DS), Antennas
    (transmit/receive), Radio transmitter/receiver (core wireless
    function), LED indicators (Power/Wi-Fi/Internet status)

### 5.4.2 — Frequency Bands

- Channels = subdivisions of a frequency band, act like lanes to avoid
    interference

- Channel bonding = combining channels for more width/throughput, at
    cost of total available channels

- 2.4 GHz: longest range, fewer channels, most congestion (shares with
    Bluetooth, microwaves), lower max data rate

- 5 GHz: shorter range than 2.4, more channels, less congestion,
    higher data rate

- 6 GHz: shortest range, fastest speed, least congestion (newest band)

- Nominal indoor range: 2.4GHz=45m/150ft, 5GHz=30m/100ft,
    6GHz=15m/50ft; real full-speed range ≈1/3 to 1/2 of nominal

### 5.4.3 — IEEE 802.11a

- 802.11a = 5 GHz only, max 54 Mbps; 23 non-overlapping channels, 20
    MHz wide each

- DFS (Dynamic Frequency Selection) = REQUIRED for 5GHz devices —
    protects radar/satellite systems

- DFS detects radar → automatically disables affected channels

- U-NII sub-bands (5MHz each) combine (x4) into 20MHz channels:
    U-NII-1(36-48), U-NII-2(52-64), U-NII-2 Ext(100-140),
    U-NII-3(149-161)

- DFS range = U-NII-2 + U-NII-2 Extended only

### 5.4.4 — IEEE 802.11b/g

- 802.11b: 2.4GHz, 11 Mbps max; 14 channels possible, 5MHz spacing;
    only channels 1/6/11 non-overlapping

- Regional limits: Americas 1-11, Europe 1-13, Japan all 14

- 802.11g: same 54Mbps/encoding as 802.11a, but on 2.4GHz → backward
    compatible with 802.11b

- 802.11b modulation = DSSS (22MHz channel, spreads signal); 802.11g
    modulation = OFDM (20MHz, more efficient)

### 5.4.5 — 802.11n (Wi-Fi 4)

- Dual-band capable (2.4GHz + 5GHz), separate radio per band; some
    older adapters are 2.4GHz-only

- Channel bonding = 2 adjacent 20MHz → 40MHz channel; mainly practical
    in 5GHz

- MIMO = multiplexes signal streams across 2-3 antennas → better
    reliability + bandwidth; notation 1x1/2x2/3x3

- Data rate: 72 Mbps/stream (20MHz) or 150 Mbps/stream (40MHz bonded)

- 'Nxxx' marketing = combined theoretical max across both radios
    simultaneously (e.g. N600 = 300+300)

- Officially renamed Wi-Fi 4

### 5.4.7 — Wi-Fi 5 and Wi-Fi 6

- Wi-Fi 5 (802.11ac): 5GHz only; dual-band AP = 2.4GHz legacy + 5GHz;
    tri-band = 1x2.4GHz+2x5GHz radios

- Wi-Fi 5: up to 8 streams theoretical, 4x4 typical; 433 Mbps/stream @
    80MHz; supports 80/160MHz bonded channels

- AC/AX marketing numbers = sum of all radios — NOT literal real
    speed, only relative comparison

- MU-MIMO (Wi-Fi 5) = downlink only, AP→up to 4 clients simultaneously

- 802.11ac doubled MIMO streams from 4 (802.11n) to 8; max speed 2.6
    Gbps

- Wi-Fi 6 (802.11ax): 600 Mbps/stream @ 80MHz; works 2.4GHz + 5GHz

- Wi-Fi 6E = adds 6GHz band support; less range, more frequency space,
    easier wide channels

- Wi-Fi 6: up to 8 simultaneous clients (vs Wi-Fi 5's 4); adds uplink
    MU-MIMO

- OFDMA = slices channel for multiple clients simultaneously; works
    alongside MU-MIMO

### 5.4.8 — Wi-Fi 7 (802.11be)

- Works across 2.4GHz, 5GHz, AND 6GHz; 6GHz channels up to 320MHz wide
    → up to 46 Gbps

- MLO (Multi-Link Operation) = device connects/sends across multiple
    bands/channels simultaneously

- MRUs (Multi-Resource Units) = 6GHz channels broken into
    dynamically-sized sub-channels, allocated per-device based on need

### 5.4.9 — Wireless LAN Installation Considerations

- SSID: network name, max 32 bytes; use ASCII
    letters/digits/hyphen/underscore for compatibility

- Same SSID both bands = auto-probe picks strongest signal; separate
    SSIDs = user manually picks band

- Operation mode = controls legacy device compatibility; supporting
    older standards can slow down ALL connected clients

- Overlapping AP coverage → use nonoverlapping channels; auto-channel
    selection exists but isn't always reliable

- Channel bonding = more bandwidth but more interference risk; mainly
    practical in 5GHz

### 5.4.10 — Wi-Fi Analyzers

- Measures signal strength (dBm, ratio to 1mW, 0dBm=1mW); closer to 0
    = better; ~-65dBm=good; worse than -80dBm=packet loss risk

- dB = logarithmic scale — +3dB=double power, -3dB=half power

- SNR = signal dBm minus noise dBm; bigger SNR = better; for noise,
    closer to 0 = WORSE

- Client hardware capability can exceed what's usable if the AP
    itself supports an older standard

### 5.4.11 — Long-Range Fixed Wireless

- Point-to-point line-of-sight: high-gain (directional) microwave
    antennas, precisely aligned, up to ~30 miles if unobstructed

- Licensed spectrum: exclusive purchased rights (FCC in US); legal
    recourse against interference

- Unlicensed spectrum: public bands (900MHz/2.4GHz/5GHz), open to
    anyone, interference risk

- Transmit power (dBm) + Antenna gain (dBi) = EIRP (dBm)

- Lower frequency = stricter power limits; highly directional antennas
    allowed higher EIRP

- Directionality (not just raw power) is why point-to-point links
    vastly outrange standard Wi-Fi APs

### 5.4.12 — Bluetooth, RFID, and NFC

- Bluetooth: radio-based, 3 Mbps base (720 Kbps actual base rate), up
    to 24 Mbps (v3/4 negotiating 802.11 link)

- Bluetooth range: earliest = 10m/30ft; newer = 100+ ft

- BLE (Bluetooth 4+) = low-power, small/infrequent data, NOT backward
    compatible w/ classic Bluetooth

- Bluetooth 5 = 240m/800ft range (4x BT4), 2x speed, 8x messaging
    capacity

- RFID: reader scans tag; Passive = unpowered, ~25m range; Active =
    powered, 100m range

- NFC = peer-to-peer RFID (device can be both tag AND reader);
    ~2in/6cm range; used for contactless payment

**5.4.15 Lesson Review — Key Takeaways (100%)**

- 802.11ac doubled MIMO streams from 4 to 8

- 802.11a operates specifically at 5.75 GHz — this band difference
    is why it's incompatible with 802.11b/g

- Bluetooth base rate = 720 Kbps; 802.11ac max speed = 2.6 Gbps;
    802.11n max speed = 600 Mbps

- Licensed spectrum = correct choice specifically for
    exclusive/interference-free use requirement

## 5.5 — Additional Resources

### 5.5.1 — Network Switches (video recap)

- Repeater (2 ports, amplifies signal beyond 100m copper limit) → Hub
    (repeater + more ports) → Switch (replaces hub, adds intelligence)

- Switch descended from the bridge (2-port device with added
    intelligence)

- Hubs and switches look identical — only documentation tells them
    apart

- MAC table learns ONLY from incoming traffic, never outgoing

- Table starts blank → builds via observed traffic → becomes
    'converged' once all devices have communicated

- Switches = full duplex (like a phone call); Hubs = half-duplex —
    major reason switches replaced hubs

### 5.5.2 — Building Wireless Networks (video recap, 2 parts)

- True WAP = single jack, wireless-only; multipurpose home 'router'
    = router + switch + WAP combined (Layer 2 + 3)

- BSS = one AP; ESS = multiple APs working together for extended
    coverage

- Adjacent AP coverage needs overlap to avoid dead spots during
    roaming (like cell tower handoff)

- Same SSID required across all APs in an ESS for seamless roaming

- 802.3 = Ethernet (wired); 802.11 = wireless — both use MAC
    addresses, little else in common

- 802.11a: ~100ft footprint, business-suited; 802.11b: larger
    footprint, home-suited

- Backward compatibility: G does NOT work with A (different bands); N
    works with A, B, AND G

- Bluetooth = PAN; RFID = asset/anti-theft tags; NFC = contactless
    payment

- ⚠ Enable Bluetooth/NFC only when actively needed, due to known
    security risks with each

## 5.6 — Module Quiz — Key Takeaways (100%)

- FTTP/ONT 'LOS' indicator = ISP-side fiber signal loss
    specifically, not an internal network issue

- Firewall ACLs need: protocol, allow/block action, source/destination
    — NOT MAC address

- 802.3at (PoE+) comfortably covers a 20W/450mA device requirement

- Microwave 2.4GHz interference → practical fix is moving to 802.11ac
    (5GHz-exclusive), which also solves speed

- Crossover cable = confirmed T568A one end, T568B other end
