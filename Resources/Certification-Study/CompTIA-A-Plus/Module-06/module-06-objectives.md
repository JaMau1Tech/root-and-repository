# Module 6 Objectives — In-Depth

*Configuring Network Addressing and Internet Connections — CompTIA A+
Core 1 (220-1201)*

## 2.7 — Compare and contrast Internet connection types, network types,
and their characteristics

The Internet is a global network of networks, with a fiber-optic
backbone connecting Internet Exchange Points where ISPs establish
transit and peering arrangements in a tiered hierarchy. A customer
connects to their ISP's nearest Point of Presence over a point-to-point
WAN link, using a digital modem rather than the NIC and switch used on a
LAN. Many of these connection types still rely on the Public-Switched
Telephone Network, whose fiber-optic core gives way to legacy copper at
its edge — the 'last mile,' 'local loop,' or POTS. DSL exploits
the higher frequencies available on that copper phone line: ADSL is
asymmetrical (fast downlink, slow uplink, up to roughly 24 Mbps down on
ADSL2+), while symmetric DSL offers equal speeds in both directions and
suits businesses that upload as much as they download. A DSL modem uses
an RJ11 port to the phone line and an RJ45 port to the router, and a
filter or splitter at each phone jack separates voice and data signals.

Cable Internet is delivered over a hybrid fiber coax (HFC) network —
fiber at the core, coax to the premises — governed by the DOCSIS
standard, with older versions offering tens of Mbps and DOCSIS 4
reaching up to 10 Gbps down through channel multiplexing. A cable modem
connects to the local router via RJ45 and to the provider's network via
coax terminated in a screw-down F-type connector, with cable runs
aggregating at a neighborhood Cable Modem Termination System before
reaching the fiber backbone. Because last-mile copper bandwidth is the
fundamental bottleneck for both DSL and cable, providers have pursued
Fiber to the X (FTTx) upgrades: Fiber to the Curb (FTTC) extends fiber
only as far as a shared cabinet, finishing the connection to the
customer over copper using VDSL (faster than standard DSL but shorter
range, supporting up to 300 Mbps down over very short distances); Fiber
to the Premises (FTTP) runs fiber the entire way, implemented as a
Passive Optical Network where an Optical Line Terminal connects through
a splitter to an Optical Network Terminal at the customer's building,
which itself converts the optical signal to electrical and connects to
the router by RJ45 — a Loss of Signal (LOS) indicator on the ONT
specifically reports trouble on that fiber connection back toward the
provider, not anything on the customer's own LAN.

Where wired options aren't practical — rural areas or older
developments — fixed wireless fills the gap. Geostationary satellite
offers enormous coverage but suffers severe latency (600-800ms
round-trip time, versus roughly 10-20ms for DSL) because the signal must
travel to an orbit thousands of miles away, making it a poor fit for
real-time applications like video calls or gaming; a VSAT dish, once
aligned with the fixed-position satellite, needs no further realignment.
Low Earth Orbit (LEO) satellite constellations trade some of that range
for dramatically better bandwidth (5-220 Mbps) and much lower latency
(25-60ms), at the cost of needing to track moving satellites via a
motorized, phased-array, or flat-panel antenna. A WISP instead uses
ground-based, long-range, fixed point-to-point antennas requiring
unobstructed line of sight between the customer and provider antenna, on
either licensed or unlicensed spectrum. Cellular data connections (3G,
4G/LTE, 5G) extend this picture to mobile use and, increasingly, to
fixed home broadband and IoT connectivity as well — cellular
generations differ mainly in frequency bands used, peak speed, and
latency, with 5G's use of both low-band and millimeter-wave spectrum,
plus massive MIMO antenna arrays, allowing dramatically higher speeds at
the cost of far shorter range on the highest-frequency bands.

## 2.5 — Compare and contrast common networking hardware devices

Beyond the switches and access points covered in Module 5, this module
adds the router and the firewall as the key devices bridging a private
network to the wider Internet. Where a switch forwards frames using MAC
addresses within one network segment, a router forwards packets between
separate networks using IP addresses, which is why a router is the
essential intermediate system anywhere a private LAN needs to reach a
public WAN. A SOHO router typically just routes between one local
interface and one WAN interface, while enterprise networks often use
specialized router types: a LAN router divides one physical network into
multiple logical subnetworks (each its own broadcast domain, improving
both performance and — through filtering — security), while a WAN or
border router specifically forwards traffic to and from the Internet or
a private WAN link, pairing an Ethernet interface for the LAN side with
a digital modem interface for the WAN side. A typical router's physical
components include ventilation ports (never to be blocked), a WAN port
bridging to the ISP, a reset button that restores factory defaults
(erasing all custom configuration), a wireless antenna (sometimes
internal and not visible), and a set of status LEDs for power, PoE, and
per-port link activity.

A firewall complements the router by filtering which hosts and traffic
types are actually allowed through, using rules organized into an Access
Control List (ACL) — each entry specifying source and/or destination
addresses, a protocol, and an allow or block action. Firewalls aren't
limited to the boundary between public and private networks; they can
also be deployed inside a private network, for instance placing a
sensitive group of servers behind their own firewall so only specific
clients can reach them. Most routers include some basic firewall
functionality, but dedicated standalone appliances can perform much
deeper inspection of application-layer data and apply more sophisticated
rules, often bundled as part of a broader Unified Threat Management
(UTM) appliance; a personal or software firewall, by contrast, protects
only the single computer it's installed on rather than an entire
network segment.

## 2.1 — Compare and contrast TCP and UDP ports, protocols, and their
purposes

The Transport layer's core job is letting a single host manage many
simultaneous connections to many different applications at once, which
it does by assigning each application a port number between 0 and 65535
(a range set by the 16-bit width of the port field itself). Well-known
ports (0-1023) are reserved for standardized protocols like HTTP on port
80; registered ports (1024-49,151) can be claimed by a vendor for their
own software, such as an antivirus company registering a specific port
for its update service; and dynamic ports (49,152-65,535) are what a
client randomly assigns itself as the source port for an outgoing
connection. Every conversation actually uses two ports per host: a
client requesting a web page sets its destination port to 80 and picks a
random dynamic source port (say, 50000); the server then replies using
port 80 as its own source and the client's original 50000 as its
destination — this swap is what lets one host track many simultaneous
'conversations' with the same protocol at once, such as several
browser tabs open to the same site.

TCP and UDP implement this port-assignment function differently. TCP is
connection-oriented: it opens a session with a three-way handshake (SYN,
then SYN/ACK, then ACK), tracks every packet with a sequence number,
uses acknowledgments to confirm receipt and can force retransmission of
anything lost or out of order, and closes the session gracefully with a
FIN handshake — all of which adds at least 20 bytes of overhead per
packet, but makes TCP the only realistic choice for protocols like HTTPS
or SSH, where a single missing or corrupted packet (especially once
encryption is involved) can break the entire exchange rather than just
cause a minor glitch. UDP strips all of that away: it's connectionless,
with no sequencing or acknowledgment and no delivery guarantee, trading
reliability for speed and lower overhead. This makes UDP the right fit
for time-sensitive traffic like voice or video, where a dropped packet
shows up as a brief glitch rather than a crashed connection, and it's
also required by protocols like DHCP that rely on broadcast
transmission, since TCP has no mechanism for broadcasting at all —
DHCP compensates for UDP's unreliability simply by having the client
retry the request if no response arrives. TFTP is another UDP-based
protocol, implementing its own acknowledgment scheme at the application
layer instead of relying on TCP's.

Real network traffic is built from packets: large chunks of data are
broken into smaller pieces, each wrapped in a packet with a header
identifying the sender, receiver, and that packet's place in the
sequence, which is exactly what lets a receiving host reassemble
everything correctly and lets a network handle traffic from many devices
at once rather than being monopolized by one giant transfer. A tool like
Wireshark makes this entire process directly observable: it captures
live traffic and displays the overall flow, the individual header fields
at each layer, and — for unencrypted protocols — the actual payload
content, which is exactly how something like a plaintext FTP password
can be captured in the clear, underscoring why encrypted alternatives
like HTTPS and FTPS (both built on TLS) matter regardless of how strong
the underlying password itself is.

A short list of well-known ports comes up constantly in real support
work: FTP uses two ports, 21 for control and 20 for the actual data
transfer; SSH (port 22) and Telnet (port 23) both provide command-line
access, secure and insecure respectively; SMTP (port 25) sends email;
DNS (port 53) resolves names, and is one of the few protocols that can
run over either TCP or UDP; DHCP uses UDP ports 67 (server) and 68
(client); HTTP (port 80) and HTTPS (port 443) form another
secure/insecure pair for web traffic; POP3 (port 110) downloads mail and
typically removes it from the server, while IMAP (port 143) instead
keeps mail on the server so multiple devices can stay synchronized; SMB
(port 445, also called CIFS) handles Windows file and printer sharing;
and RDP (port 3389) provides secure remote access to a Windows graphical
desktop.

## 2.3 — Summarize services provided by networked hosts

DHCP (Dynamic Host Configuration Protocol) automates what static
configuration does manually and error-pronely: assigning an IP address,
subnet mask, default gateway, and DNS servers. A DHCP server is
configured with a scope — a range of addresses it's permitted to hand
out, deliberately excluding any statically-assigned addresses such as
its own. The lease process follows four steps known by the acronym DORA:
the client broadcasts a DHCPDISCOVER message (since it has no address
yet, and doesn't need to know the server's address in advance); an
available server replies with a DHCPOFFER proposing an address and
configuration; the client broadcasts a DHCPREQUEST accepting that offer
(still broadcast, so any other servers that made competing offers know
to withdraw them); and the server finalizes everything with a DHCPACK.
All of this happens over UDP, with the server listening on port 67 and
the client on port 68. As a final safety check, the client ARPs the
address it was just given to confirm nothing else on the network is
already using it before actually starting to use it itself. Addresses
are leased for a limited time and must be renewed; if a client can't
reach a DHCP server at all, Windows machines fall back to APIPA,
self-assigning an address in the 169.254.0.1-169.254.255.254 range that
only allows communication with other APIPA-addressed hosts on the same
local segment. For devices that need a consistent address every time —
printers, servers, infrastructure — a DHCP reservation maps a specific
MAC address to a specific IP within the server's own configuration,
avoiding the need to manually configure static addressing on each
individual device.

DNS (Domain Name System) exists because IP addresses are impractical for
people to remember, so a friendly host name is assigned to each device
instead; combined with a domain name and top-level domain, this becomes
a Fully Qualified Domain Name (FQDN) that's globally unique. DNS itself
is a distributed, hierarchical database, rooted at a null label
(represented by a trailing period) served by 13 root servers, below
which sit top-level domains — generic (.com, .org, .net), sponsored
(.gov, .edu), and country-code (.uk, .ca) — managed overall by ICANN.
When a user's browser (acting as a 'stub resolver') needs to resolve
a name, it first checks its local cache, then queries its configured DNS
server over port 53. An authoritative name server for a given domain
holds that domain's actual resource records, most commonly A records
(hostname to IPv4 address), AAAA records (hostname to IPv6 address),
CNAME records (aliasing one domain name to another, useful for something
like redirecting an acquired company's old website without maintaining
two separate sites), MX records (identifying a domain's mail server,
with a lower preference number meaning higher priority, and always
requiring an associated A or AAAA record for the mail server's actual
hostname), and PTR records (the reverse of an A record — given an IP
address, returning the associated hostname, useful for investigating a
suspicious IP on the network). TXT records hold arbitrary free-form text
and are the basis for three layered anti-spam and anti-spoofing
frameworks: SPF (one record per domain, listing which hosts are
authorized to send mail on the domain's behalf, with a policy for what
to do with mail from unauthorized senders); DKIM (publishing a public
cryptographic key so recipients can verify a message's signature
actually matches the claimed sending domain); and DMARC (specifying how
to handle SPF or DKIM authentication failures — flagging,
quarantining, or rejecting the message — and how failures should be
reported back to the sender).

VLANs and VPNs both extend what a basic network of switches and routers
can do. A VLAN (Virtual LAN) is a managed-switch feature that logically
divides a set of ports — and therefore the hosts connected to them —
into separate broadcast domains identified by a VLAN ID between 2 and
4094 (with ID 1 reserved as the default that all ports belong to unless
reconfigured). Hosts in different VLANs cannot communicate directly even
when plugged into the very same physical switch; each VLAN needs its own
subnet, its own DHCP service, and its own DNS service, and any traffic
that needs to cross between VLANs must pass through an IP router, which
is also where that inter-VLAN traffic can be filtered and monitored for
security purposes — VLANs are also commonly used to isolate specific
traffic types, such as giving voice traffic its own VLAN so it can be
prioritized over ordinary data. A VPN (Virtual Private Network), by
contrast, extends a private network out over the public Internet rather
than segmenting it: a remote host connects to a VPN gateway, which
authenticates the user and establishes an encrypted tunnel, after which
the remote computer functions as though it were physically part of the
local network (limited only by the available Internet bandwidth). Every
packet sent through that tunnel is both encrypted and encapsulated
inside another packet, so that even if the traffic is intercepted
somewhere along its path, its actual contents remain unreadable. Beyond
simple remote access for individual users, VPNs are also used to link
entire sites together over a public network — connecting a branch
office to a company's head office — or even deployed within a single
local network as an additional layer of security.

## 2.4 — Explain common network configuration concepts

Configuring a host or a network for actual use goes well beyond simply
assigning an address. The foundational choice is static versus dynamic
addressing: static configuration is entered by hand on each device —
appropriate for systems needing a fixed, predictable address, like a
router interface or a server, but slow and error-prone to manage at
scale, since an administrator must track every allocated address to
avoid duplicates and must revisit any device that moves to a different
network. Dynamic configuration through DHCP solves this by automatically
leasing an IP address, subnet mask, default gateway, and DNS servers to
a client through the DORA process, all bundled into the server's
configured scope so a client receives a complete, working configuration
in one exchange rather than needing each setting configured separately.

DNS configuration is the other major piece of making a network genuinely
usable rather than just technically connected: a host needs to know
which DNS server(s) to query (commonly supplied automatically via the
same DHCP scope as the IP configuration), and a domain's authoritative
server needs the actual records — A, AAAA, CNAME, MX, TXT-based
SPF/DKIM/DMARC — that let other hosts resolve and trust that domain
correctly. On the addressing side, distinguishing public from private
addressing is also a core configuration concept: private RFC 1918 ranges
are used internally and never routed on the public Internet, reaching it
instead through NAT translation performed by the router or through a
proxy server acting on clients' behalf.

Segmentation and remote access round out the common configuration
concepts for this objective. VLANs let a single physical switch fabric
be divided into multiple logical, isolated broadcast domains, each
configured with its own subnet, DHCP scope, and DNS service, with a
router required to pass traffic between them — a configuration choice
made for both performance (smaller broadcast domains) and security
(filterable inter-VLAN traffic). VPNs configure a different kind of
logical boundary: rather than dividing a network, they extend it, using
a remote access server, authentication, and an encrypted tunnel to let
an outside host behave as if it were locally connected. Together,
static/dynamic addressing, DNS, public/private addressing with NAT,
VLANs, and VPNs represent the standard toolkit for configuring how a
network's hosts get addressed, how they're segmented, how they resolve
names, and how they can be reached — the practical configuration work
that sits on top of the addressing and protocol fundamentals covered
elsewhere in this module.

Learning Outcomes by Lesson

Lesson 6.1 — Internet Connection Types

**What are the various internet connection types provided by an ISP?**

DSL, cable, fiber (FTTC/FTTP), satellite (geostationary and LEO), fixed
wireless (WISP), and cellular (3G/4G/5G) — each trading off speed,
range, latency, and installation cost differently.

**What networking hardware components are used to connect to an ISP?**

A digital modem (DSL, cable, or an ONT for fiber) establishes the
physical connection to the ISP's WAN interface, and a router —
implementing IP — provides the logical forwarding between the private
LAN and the public Internet. A firewall is typically also present to
filter which traffic is allowed to cross that boundary.

**What are IPv4 and IPv6, and how do they allow various networks to
communicate?**

IPv4 is a 32-bit addressing scheme written in dotted decimal notation;
IPv6 is a 128-bit scheme written in hexadecimal. Both encode a network
portion and a host portion within the address, letting routers determine
whether a destination is local (same network) or needs to be forwarded
elsewhere (different network) — this addressing and forwarding logic
is what lets independently-designed networks communicate as one larger
internetwork.

**What are TCP and UDP communications protocols, and how are they
different from one another?**

TCP and UDP are the two Transport layer protocols. TCP is
connection-oriented and reliable, using a handshake, sequencing, and
acknowledgments to guarantee delivery — used by most applications. UDP
is connectionless and unreliable but much faster, used for
time-sensitive applications like voice and video where occasional data
loss is an acceptable tradeoff for speed.

**What ports and protocols are commonly found on SOHO and ISP
networks?**

Common ports include 53 (DNS), 67/68 (DHCP), 80/443 (HTTP/HTTPS), 25
(SMTP), 110/143 (POP3/IMAP), 445 (SMB), and 3389 (RDP) — each tied to
a specific well-known protocol that identifies its traffic type to a
firewall or switch.

**How do DNS and DHCP assist in the configuration of a network?**

DHCP automatically assigns each host its IP address, subnet mask,
gateway, and DNS servers, removing the need for manual per-device
configuration. DNS then lets those hosts (and everyone else on the
Internet) refer to each other by friendly names instead of numeric
addresses, resolving those names to the correct IP through a
distributed, hierarchical system of authoritative servers.
