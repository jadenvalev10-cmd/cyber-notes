# TryHackMe: Extending Your Network

Pre Security path, Network Fundamentals module. September 2026.

**Situation:** Room on the technologies used to extend a LAN onto the Internet, with a firewall practical and a network simulator.

**Task:** Understand port forwarding, firewalls, VPNs, and LAN devices, and apply them in the practicals.

**Action:**

- Task 1, port forwarding: configured on the router to open specific ports so an internal service (such as a web server on port 80) is reachable through the network's public IP. It differs from a firewall, which decides whether traffic may cross those ports.
- Task 2, firewalls: permit or deny traffic by source, destination, port, and protocol (packet inspection), operating at OSI layers 3 and 4.
  - Stateful: inspects the whole connection. More resource-heavy, but can block a bad host outright.
  - Stateless: static rules applied to each packet. Lightweight, and good against floods such as DDoS.
- Task 3, practical: configured firewall rules to block malicious traffic on port 80 to a web server.
- Task 4, VPNs: an encrypted tunnel between separate networks. Connects distant sites, protects against sniffing on public Wi-Fi, and gives some anonymity.
- Task 5, LAN devices: routers (Layer 3, choose the best path between networks), Layer 2 switches (forward frames by MAC address), Layer 3 switches (also route by IP), and VLANs (virtually split a network for security and separation).
- Task 6, network simulator: sent a TCP packet between computers and read the network log.

**Result:** Worked through all six tasks.

**Key terms**

port forwarding, router, firewall, stateful, stateless, packet inspection, VPN, tunnel, Layer 2 vs Layer 3 switch, VLAN, routing
