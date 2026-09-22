# Module 5 Objectives — In-Depth

*Comparing Local Networking Hardware — CompTIA A+ Core 1 (220-1201)*

## 2.7 — Compare and contrast Internet connection types, network types,
and their characteristics

A LAN (Local Area Network) connects computers via cabling and one or
more network switches, all confined to a single geographical location
— anywhere nodes sit within roughly 1-2 kilometers counts as 'local'
— and LAN infrastructure is typically owned and managed directly by
the organization using it. Most cabled LANs are built on IEEE 802.3
Ethernet standards, named in the format xBASE-Y: 100BASE-T runs Fast
Ethernet at 100 Mbps over copper, 1000BASE-T runs Gigabit Ethernet at
1000 Mbps and is the mainstream standard for most LANs today, and
10GBASE-T pushes copper to 10 Gbps. Most LANs use copper cabling, while
a LAN's backbone or specialized high-throughput segments often use
fiber optic cabling instead.

A WAN (Wide Area Network) spans multiple geographic locations rather
than a single site — the Internet itself is the ultimate example. An
ISP is a company that facilitates access from local networks out to the
Internet, and most private or enterprise WANs use cabling and equipment
leased from an ISP to interconnect multiple LAN sites, such as
connecting branch offices back to a company's head office LAN. A WLAN
uses radios and antennas instead of cabling, based on IEEE 802.11,
better known as Wi-Fi; Wi-Fi and Ethernet frequently coexist as segments
of the same overall LAN.

A MAN (Metropolitan Area Network) covers an area equivalent to a city
— larger than a single LAN but smaller than a full WAN — and often
describes a company's multiple connected networks spread across one
metro area. A PAN (Personal Area Network) is wireless connectivity at a
range of just a few meters, connecting a phone or PC to wearables or
peripherals; the classic example is Bluetooth earbuds and a smartwatch
both connected to a person's phone. A SAN (Storage Area Network) is a
specialized network dedicated entirely to storage devices, letting
servers connect to storage as if it were directly attached; it runs on a
dedicated network independent of the regular LAN, moves data as raw
blocks with no file system structure, consolidates multiple storage
types into centralized shared resources, and relies on high-speed
connections like Fibre Channel or iSCSI.

Network scale also determines architecture. A SOHO network is small,
usually consolidating LAN and Internet connectivity into a single
all-in-one appliance (a 'SOHO router'), where the router handles both
public and private functions, switch ports and a wireless access point
create the local private network, and the router's built-in modem
connects out to the ISP. An enterprise network delivers the same
underlying functions but, because it must support far more clients with
greater reliability, splits each function into its own dedicated device
— each network segment is designed as a modular function. A typical
enterprise layout routes client computers through wall ports and cabling
to a patch panel and then workgroup switches, while laptops connect
wirelessly through access points that also link back to those same
workgroup switches; workgroup switches then connect up to
core/distribution switches, routers, and firewalls, which manage
authorized connections out to servers, a DMZ, remote access/VPN, and the
ISP. Internet-facing services live in a DMZ — a protected, screened
subnet acting as the border between the private LAN and the public
Internet, with traffic strictly filtered and monitored.

On an enterprise LAN, servers are typically isolated in a dedicated
server room, distinct from client computers which let end users access
those shared resources. When server requirements grow large enough, an
organization may instead operate a full datacenter: an entire site
dedicated to provisioning server resources, usually housed in a
purpose-built facility with dedicated networking, dedicated power,
climate control, and physical access control all engineered together to
deliver high availability for critical applications. Choosing the right
network type for a given need is fundamentally about matching
infrastructure complexity to actual scale of need.

## 2.5 — Compare and contrast common networking hardware devices

A NIC (Network Interface Card) is the physical connection point for
Ethernet, using a transceiver port to send electrical signals over
copper or light pulses over fiber; most motherboards include a built-in
1000BASE-T compatible adapter, and multiple NIC ports can be bonded
together into a single, faster logical link. Every Ethernet NIC port
carries a unique hardware MAC address, 48 bits written as 12 hexadecimal
digits, split into a 24-bit OUI identifying the manufacturer and a
24-bit NIC-specific portion uniquely identifying that individual
interface.

A switch connects multiple devices within the same network and is the
descendant of the older bridge, which added intelligence that a simple
hub or repeater never had. A switch builds a MAC address table
dynamically, learning only from the source address of incoming frames
— never from a destination address, since it doesn't yet know where
an unlearned device lives. Using that table, the switch forwards each
frame only out the port matching its destination MAC address rather than
broadcasting it everywhere; if the destination isn't yet known, the
switch floods the frame out every port except the one it arrived on,
learning the correct location once that device responds. This behavior
gives each switch port its own separate collision domain, eliminating
the collisions that plagued older shared-media hubs, and lets every
connected device operate in full duplex, sending and receiving
simultaneously at full speed, similar to two people on a phone call who
can both talk and listen at once. Switches exist in two tiers: unmanaged
switches require no configuration at all and are common in SOHO routers,
while managed switches work the same way out-of-the-box but can be
configured over a dedicated management port for security settings and
advanced features, and are typically rack-mounted with 24 or 48 ports
plus uplink ports for connecting to other switches. At the largest
scale, modular switches share a common power supply and a fast
communications backplane to interconnect multiple switch units,
provisioning hundreds of access ports from a single compact chassis.

A router is a fundamentally different device from a switch: where a
switch connects devices within one network, a router forwards traffic
between separate networks, making it the device responsible for
connecting a LAN to a WAN or the Internet. An access point (AP) provides
wireless connectivity, most commonly operating in infrastructure mode,
where client devices (stations) connect through the AP rather than
directly to each other; this arrangement is called a Basic Service Set
(BSS), identified by the AP radio's MAC address as the BSSID. An AP can
bridge wireless clients to a wired distribution system through its own
Ethernet port, and multiple APs working together to extend coverage form
an Extended Service Set (ESS) — adjacent APs' coverage areas need
deliberate overlap and must share the same SSID so a moving client can
roam seamlessly from one AP to the next without disassociating, the same
principle behind a cell phone handing off between cell towers.

A patch panel is the organizational hub of structured cabling:
permanent, in-wall cabling terminates at insulation displacement
connector (IDC) punchdown blocks on the panel's rear, while pre-wired
RJ45 ports on the front connect via a short patch cord to an Ethernet
switch. This design means reconfiguring which wall port reaches which
part of the network is as simple as moving a patch cord, without ever
touching the permanent cabling inside the walls, and it also protects
the more expensive switch ports from the physical wear of repeated
reconnection. A network tap is a different kind of hardware, used
specifically to intercept and copy signals passing over a cable for
monitoring or analysis: a passive tap physically copies the signal with
an inductor or optical splitter and needs no power, capturing every
frame regardless of load, while an active tap is powered and performs
signal regeneration, necessary for Gigabit copper or certain fiber
types, at the cost of becoming a point of failure for the link if it
loses power. An alternative to a physical tap is a SPAN or mirror port,
a specially configured switch port that receives copies of frames from
other nominated ports without any separate hardware device.

Power over Ethernet (PoE) lets a switch deliver electrical power to a
device over the same cable carrying data, eliminating the need for a
separate power adapter at devices like VoIP phones, cameras, and access
points. A PoE-enabled switch, called endspan power sourcing equipment,
first detects whether a connected device is actually PoE-capable before
supplying any power, protecting non-PoE devices from damage. When a
switch doesn't support PoE natively, a PoE injector (or midspan device)
can add power into an existing Ethernet run between the switch and the
device, though the overall cable length is still capped at the standard
100 meters.

## 2.8 — Explain networking tools and their purposes

Installing structured copper cabling requires a specific tool sequence.
A cable stripper scores and removes a section of the outer jacket
without damaging the inner wire pairs' insulation; Cat 6 and 6A cables
additionally contain a plastic star filler that must be snipped off with
electrician's scissors before termination. A punchdown tool presses
each untwisted wire into a color-coded IDC terminal, where small blades
cut through the wire's insulation to make electrical contact — no
more than half an inch of wire should be left untwisted at this point,
since excess untwisting increases the risk of crosstalk between pairs. A
crimper attaches an RJ45 plug to a patch cord: the plug is oriented with
its tab latch facing down, wires are arranged in the correct T568A or
T568B order and pushed in, and the crimper then pierces the wire
insulation at each pin while sealing the plug to the outer jacket for
strain relief.

Once cable is terminated, it must be tested immediately, while there's
still access to the run, since errors are far easier to fix at that
stage than after end-user devices are connected. A cable tester attaches
to both ends of a cable and energizes each wire in turn, lighting an LED
for each successful connection; a wire that doesn't light up usually
has damaged insulation or wasn't properly seated, and if the LEDs light
in a different sequence at each end, the two ends were wired to
different pins and need to be corrected to match. A toner probe, often
built into the same device as a cable tester, helps identify one
specific cable within an unlabeled bundle: a tone generator applies a
continuous audio signal to the cable, and a probe detects that tone to
trace the cable through walls, ceilings, or a tangle of similar-looking
cables — the far end should be disconnected from any live equipment
first. A loopback plug tests a NIC, switch port, or serial/parallel port
directly rather than testing cable: a simple DIY version wires pin 1 to
pin 3 and pin 2 to pin 6 in a short cable stub, and a solid link LED
after connecting it confirms the port can both send and receive, though
this simple version generally won't work on Gigabit ports, which
require a purpose-built Gigabit loopback tester instead.

A network tap and a Wi-Fi analyzer both serve a monitoring purpose but
for different media. A network tap intercepts and copies wired signals
for a packet or protocol analyzer, in either a passive (unpowered,
physical copy) or active (powered, signal-regenerating) form. A Wi-Fi
analyzer, hardware or software, measures wireless signal strength in dBm
— a logarithmic ratio to one milliwatt, where values closer to zero
represent a stronger signal, roughly -65 dBm is considered good, and
anything weaker than about -80 dBm risks packet loss. The
signal-to-noise ratio (SNR), the gap in dB between the actual signal and
the background noise floor, is what really determines connection quality
— two networks can show identical signal strength but perform very
differently if their noise levels differ, since for noise specifically,
values closer to zero represent worse conditions rather than better
ones.

## 3.2 — Summarize basic cable types and their connectors, features, and
purposes (network cabling)

Unshielded Twisted Pair (UTP) is the most common network cable, built
from four copper wire pairs, each twisted at a different rate to reduce
interference; the electrical signals on each pair are also balanced,
with each wire carrying an equal but opposite signal to its partner,
which further helps the receiving end distinguish real signal from
noise. UTP suffers attenuation over distance and is capped at a
100-meter maximum recommended run. Shielded Twisted Pair (STP) adds
extra protection for environments with high electromagnetic
interference, such as cabling near fluorescent lighting, power lines,
motors, or generators, and comes in several forms: F/UTP has a single
foil shield around all pairs at a reasonable cost, S/FTP (or F/FTP) adds
both a braided or foil outer shield and individually shielded pairs for
the best protection at a higher cost and reduced flexibility, and U/FTP
shields each pair individually with no outer shield at all. Any
shielding must be properly bonded to the connector, or the shield itself
can act like an antenna and generate interference rather than blocking
it.

Cable performance is standardized by Category (Cat) rating under
TIA/EIA-568-C, printed directly on the cable jacket: Cat 5 (100 Mbps,
now obsolete), Cat 5e (1 Gbps), Cat 6 (1 Gbps at the full 100 meters, or
10 Gbps at a reduced 55 meters), Cat 6A (a full 10 Gbps at 100 meters,
though bulkier and recommended by TIA/EIA for healthcare facilities, PoE
802.3bt installations, and wireless access point cabling), and Cat 7/Cat
8, which support 10-40+ Gbps over short runs and are mainly found in
data centers today. Cat 7 requires GG45 or TERA connectors to achieve
its full rated performance, since a standard RJ45 plug cannot deliver
the complete Cat 7 specification even though GG45 jacks can physically
accept an RJ45 plug for compatibility; Cat 8 splits into Cat 8.1, which
uses backward-compatible RJ45 connectors, and Cat 8.2, which uses
GG45/TERA connectors and is not backward compatible with RJ45 at all.

Twisted pair terminates into an RJ45 connector, formally called 8P8C
(8-position, 8-contact), following one of two wiring standards defined
under EIA/TIA-568: T568A and T568B, which differ only in whether the
orange or green pair occupies pins 1-2 and 3/6. A straight-through cable
uses the same standard on both ends and is the normal cable used to
connect a device to a switch; a crossover cable deliberately uses T568A
on one end and T568B on the other, crossing the transmit and receive
pairs so two like devices (such as two switches, or two PCs) can connect
directly without an intermediary switch — though modern NICs with
Auto-MDIX have made crossover cables largely unnecessary today, since
they can automatically detect and adjust for a straight-through cable in
that situation. RJ11, by contrast, terminates two-pair cable rather than
Ethernet's four pairs, and is used for telephone and DSL connections,
not networking.

Installing this cabling has to comply with local building and fire
codes. A plenum space — typically a false ceiling used for HVAC — is
an effective conduit for fire spread due to its airflow and lack of fire
breaks, so cable run through it must be plenum-rated:
self-extinguishing, low-smoke, made from treated PVC or FEP rather than
standard PVC (marked CMP on the jacket, versus CMG/CM for
general-purpose cable), with no difference in actual bandwidth
performance. Cable run outside a building (Outside Plant, or OSP) faces
UV exposure, temperature swings, and dampness that standard PVC cannot
handle; aerial cable strung between poles, cable in conduit, and direct
burial cable laid straight into the ground all require special UV- and
abrasion-resistant coatings, often gel-filled construction, and
sometimes rodent-resistant armoring for direct burial specifically.

Fiber optic cable carries data as light pulses rather than electrical
signals, making it immune to electromagnetic interference and far less
prone to attenuation, which lets it support much higher bandwidth over
much longer distances than copper — miles rather than feet. A fiber
strand consists of a glass core carrying the light, surrounded by
cladding that guides it, a protective buffer coating, and an outer
jacket. Single-mode fiber has a small core and uses a high-power laser
diode to carry a long-wavelength signal over many kilometers at 10 Gbps
or better, making it suited to WAN-scale links, while multimode fiber
has a larger core and uses cheaper LEDs or VCSELs to carry a
shorter-wavelength signal over shorter distances at a lower cost, making
it more suited to LANs. Fiber connectors all rely on a ceramic or
plastic ferrule for precise alignment: ST uses a bayonet twist-lock and
is mostly found on older multimode networks, SC uses a simple push/pull
design available in simplex or duplex form, LC is a smaller push/pull
connector enabling higher port density, and MPO is a wide push-on
connector that terminates many fiber strands (commonly 12 or 24) at once
for high-density data center and backbone connections. Fiber connectors
are fragile and should not be repeatedly plugged and unplugged, and
unused ports should always be covered with a dust cap to prevent
contamination that could block the light signal.

Coaxial cable is another copper cable type, but instead of twisted
pairs, it uses two conductors sharing a common axis: a central copper
conductor, surrounded by plastic dielectric insulation, surrounded in
turn by a wire mesh conductor that serves as both EMI shielding and
electrical ground. This physical shielding approach, rather than twisted
pair's balanced-signal cancellation, is how coax resists interference.
Coax today is mostly used for CCTV installations and as patch cable for
cable television and broadband cable modems, terminated with a
screw-down F-type connector for CATV or a bayonet-style BNC connector
for video, radio, and television applications.

## 2.2 — Explain wireless networking technologies

Wireless networking uses radio waves as its transmission medium, with
antennas tuned to specific frequencies. Most Wi-Fi networks run in
infrastructure mode, where every client device (a station) connects to
the network through an access point rather than directly to other
stations, forming what 802.11 documentation calls a Basic Service Set
(BSS), identified by the AP radio's MAC address as the BSSID. An AP can
operate wireless-only or bridge those wireless clients to a wired
distribution system, and multiple APs working together with the same
SSID form an Extended Service Set (ESS), with deliberately overlapping
coverage so a moving device can roam from one AP to the next without a
dead spot or forced re-association — the same principle behind a cell
phone handing off between towers.

Every wireless frequency band is divided into channels, narrower slices
that let multiple networks share a band without interfering, and some
standards allow adjacent channels to be bonded into a wider one for more
throughput at the cost of fewer total available channels. Wi-Fi operates
across three main bands, and the tradeoff across all three follows the
same pattern: 2.4 GHz penetrates solid surfaces best and has the longest
range, but has few channels and shares the band with Bluetooth,
microwave ovens, and other 2.4 GHz networks, resulting in the most
congestion and lowest data rates; 5 GHz has shorter range but far more
channels and less congestion, supporting higher data rates; and 6 GHz,
the newest band, has the shortest range but the most available frequency
space and, currently, the least congestion, enabling the fastest speeds.
Devices operating in the 5 GHz band must implement Dynamic Frequency
Selection (DFS) to automatically disable channels if nearby radar is
detected, since 5 GHz overlaps frequencies used by radar and satellite
systems — this requirement specifically covers the U-NII-2 and U-NII-2
Extended channel ranges, not the entire band.

The Wi-Fi standards themselves evolved to solve one limitation after
another. The original 802.11a (1999) used 5 GHz for 54 Mbps but suffered
limited range, while 802.11b (also 1999) traded speed for range by
moving to 2.4 GHz at just 11 Mbps. 802.11g (2003) combined 802.11a's 54
Mbps encoding with 802.11b's 2.4 GHz band, making it easy to design
backward-compatible devices. 802.11n, later renamed Wi-Fi 4, introduced
two major advances: dual-band operation with a separate radio per band,
and MIMO, which multiplexes signal streams across two or three antennas
(notated 1x1, 2x2, 3x3) to improve both reliability and bandwidth,
alongside channel bonding that combines adjacent 20 MHz channels into a
40 MHz channel, mainly practical in the less-crowded 5 GHz band. Wi-Fi 5
(802.11ac) moved exclusively to 5 GHz, doubled MIMO streams from four to
eight, added still-wider 80 and 160 MHz bonded channels, and introduced
downlink MU-MIMO, letting an AP serve up to four clients simultaneously
instead of queuing them one at a time — a real-world example of when
to choose it is replacing an AP suffering 2.4 GHz microwave
interference, since Wi-Fi 5's 5 GHz-only design sidesteps that
interference source entirely while also increasing speed. Wi-Fi 6
(802.11ax) pushed per-stream throughput further, added support for up to
eight simultaneous clients, introduced uplink MU-MIMO so clients can
send data to the AP simultaneously as well, and added OFDMA, which
slices a channel into smaller allocations so many clients can share it
efficiently even without separate antenna streams; Wi-Fi 6E extends this
into the new 6 GHz band. Wi-Fi 7 (802.11be) works across all three bands
at once through Multi-Link Operation, uses channels up to 320 MHz wide
in the 6 GHz band for theoretical speeds up to roughly 46 Gbps, and
introduces Multi-Resource Units, which dynamically size 6 GHz
sub-channels per device based on actual bandwidth need.

Configuring a wireless network involves several linked decisions. An
SSID identifies the network to clients and should stick to ASCII
letters, digits, hyphens, and underscores for compatibility; using the
same SSID on both bands of a dual-band AP lets devices automatically
connect to whichever band has the stronger signal, while separate SSIDs
let the user choose manually. The operation mode set per band controls
compatibility with older client devices, but supporting legacy standards
can reduce performance for every connected client, not just the older
device. Overlapping APs should use non-overlapping channels to avoid
interference (in 2.4 GHz, this means channels 1, 6, and 11
specifically), and while channel bonding increases bandwidth, it also
raises interference risk and is generally only practical in the 5 GHz
band. A Wi-Fi analyzer, hardware or software, is the tool used to
actually measure this: it reports signal strength in dBm (closer to zero
is better, around -65 dBm is considered good, and below -80 dBm risks
packet loss) and calculates the signal-to-noise ratio, the gap between
signal and background noise that ultimately determines real connection
quality more than signal strength alone.

Beyond standard Wi-Fi, long-range fixed wireless can bridge two networks
over distance without cabling. Point-to-point line-of-sight links use
precisely aligned, highly directional (high-gain) microwave antennas,
reaching up to roughly 30 miles when unobstructed. These links can run
on licensed spectrum, where an operator purchases exclusive rights to a
frequency band from a regulator (the FCC in the US) and has legal
recourse against interference — the right choice whenever guaranteed,
interference-free operation matters, such as a rural point-to-point link
between two company buildings — or on unlicensed public spectrum (900
MHz, 2.4 GHz, 5 GHz), which anyone can use and which therefore carries
real interference risk. A signal's total power is described by transmit
power (the radio's base strength, in dBm), antenna gain (the boost from
directionality, in dBi), and EIRP (the sum of the two, in dBm);
regulations generally allow a highly directional antenna a higher EIRP
in exchange for lower transmit power, which is exactly why a focused
point-to-point link can travel dramatically farther than an ordinary
omnidirectional Wi-Fi AP on comparable power.

Finally, several shorter-range wireless technologies implement personal
area networking rather than LAN-style host networking. Bluetooth
connects peripherals and shares data at a base rate around 720 Kbps,
reaching up to 24 Mbps on versions 3/4 by negotiating an 802.11 radio
link for large transfers, with range growing from an original 10 meters
up to Bluetooth 5's 240 meters (roughly four times Bluetooth 4's
range, at twice the speed and eight times the messaging capacity);
Bluetooth Low Energy (introduced in version 4) targets small,
battery-powered devices sending infrequent small amounts of data, and is
not backward compatible with classic Bluetooth even though a device can
support both simultaneously. RFID identifies and tracks objects through
encoded tags that respond when scanned — passive tags are unpowered
with roughly a 25-meter range, while active tags are powered with up to
100 meters, commonly used in shipping labels and access badges. NFC is
essentially a peer-to-peer version of RFID, where a device can act as
both tag and reader at a range of only a couple of inches, making it the
standard technology behind contactless payment, along with security tags
and retail shelf-edge labels.

Learning Outcomes by Lesson

Lesson 5.1 — Network Types

**What is a network that covers the area equivalent to a city known
as?**

A MAN (Metropolitan Area Network) — larger than a single LAN, smaller
than a full WAN, typically describing a company's connected networks
spread across one metro area or city.

**A user has connected a smartwatch and earbuds to their cellphone over
Bluetooth. What type of network have they created?**

A PAN (Personal Area Network) — wireless connectivity at a range of
just a few meters, connecting wearables and peripherals to a central
device like a phone.

**You have been tasked with creating a network in which each segment of
the network is designed as a modular function. What type of network are
you creating?**

An enterprise network — unlike a SOHO setup that consolidates every
function into one device, an enterprise network separates routing,
switching, wireless access, and server resources into distinct,
purpose-built components for scalability and reliability.

**What is a whole site that is dedicated to provisioning server
resources called?**

A datacenter — typically a purpose-built facility with dedicated
networking, power, climate control, and physical access control, built
for high availability of critical applications.

**Which IEEE Ethernet standards are most cabled LANs based on?**

IEEE 802.3, the standard family governing Ethernet — named in the
xBASE-Y format, with 1000BASE-T being the mainstream choice for most
LANs today.

Lesson 5.3 — Network Cable Types

**What type of network cable should be used in environments with high
levels of external interference?**

Shielded Twisted Pair (STP), in one of its forms (F/UTP, S/FTP, or
U/FTP) — the shielding physically blocks EMI from sources like
fluorescent lighting, power lines, motors, and generators.

**Which Ethernet Cat standard can provide a maximum transfer rate of 25
Gbps over a maximum distance of 30 meters?**

Cat 8 — specifically the 25GBASE-T specification, which delivers 25
Gbps at up to 30 meters (Cat 8 also supports 40 Gbps at the same
30-meter distance).

**What type of connector does a Cat 7 cable use?**

GG45 or TERA connectors, per ISO/IEC standards — a standard RJ45 plug
can physically fit a GG45 jack for compatibility, but cannot deliver the
full Cat 7 specification.

**What is the order of wires in a T568B cable?**

Pin 1: Orange/White, Pin 2: Orange, Pin 3: Green/White, Pin 4: Blue, Pin
5: Blue/White, Pin 6: Green, Pin 7: Brown/White, Pin 8: Brown.

**Which tool is used to fix a RJ45 jack to a patch cord?**

The crimper — it pierces the wire insulation at each pin position and
seals the plug body to the outer cable jacket for strain relief.

**Which cable type transfers data using light?**

Fiber optic cable — light pulses generated by lasers or LEDs travel
through a glass core, rather than electrical signals traveling through
copper.

Lesson 5.4 — Wireless Networking Types

**What type of mode are most wireless networks configured in?**

Infrastructure mode — client stations connect to the network through
an access point rather than directly to one another.

**What are the three main frequency bands used by wireless networks?**

2.4 GHz, 5 GHz, and 6 GHz.

**Your wireless network has been running slow, and analysis shows
multiple networks on the same frequency. What's the best solution?**

Reconfigure the access point to use a different, non-overlapping channel
(or move operation to a less congested band, such as 5 GHz or 6 GHz) —
the slowdown is caused by channel congestion/interference from the
overlapping networks, not a hardware fault.

**What technology increases reliability and bandwidth by multiplexing
signal streams from multiple antennas?**

MIMO (Multiple Input Multiple Output), introduced in 802.11n.

**Which wireless technology is primarily used for contactless payment?**

NFC (Near Field Communication).
