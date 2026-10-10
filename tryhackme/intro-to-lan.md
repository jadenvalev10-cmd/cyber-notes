# TryHackMe: Intro to LAN

Pre Security path, Network Fundamentals module. September 2026.

**Situation:** Room on LAN technologies and designs, with a video and an interactive topologies lab.

**Task:** Learn the main LAN topologies and their trade-offs, the roles of switches and routers, subnetting, ARP, and DHCP.

**Action:**

- Task 1, topologies:
  - Star: every device cabled to a central switch. Scalable and reliable, but costlier, and the central device is a single point of failure.
  - Bus: all devices share one backbone cable. Cheap, but bottlenecks easily and the whole segment fails if the backbone breaks.
  - Ring: devices form a loop and forward data toward its destination. Easy to troubleshoot, but one break takes the ring down.
  - Switches track which device is on which port and forward packets only to the intended port, unlike a hub, which broadcasts. Routers connect separate networks and route data between them.
  - Lab: broke each topology to see its failure behaviour.
- Task 2, subnetting: splitting a network into smaller sub-networks using a subnet mask. Covers the network address (identifies the network), host address (identifies a device), and default gateway (routes traffic off the network). Benefits are efficiency, security, and control, such as separating a café's staff network from its public Wi-Fi.
- Task 3, ARP: maps an IP address to a MAC address using an ARP cache. A device broadcasts an ARP Request ("who owns this IP?") and the owner answers with an ARP Reply containing its MAC address.
- Task 4, DHCP: automatic IP assignment in four steps: Discover, Offer, Request, ACK.

**Result:** Completed the room.

**Key terms**

LAN, topology, star, bus, ring, switch, hub, router, subnetting, subnet mask, network address, host address, default gateway, ARP, ARP cache, DHCP, DHCP Discover / Offer / Request / ACK
