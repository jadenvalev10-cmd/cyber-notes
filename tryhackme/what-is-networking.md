# TryHackMe: What is Networking?

Pre Security path, Network Fundamentals module. September 2026.

**Situation:** Intro room on core networking concepts, with a video and two interactive labs (a simulated hotel Wi-Fi with a MAC filter, and a ping terminal).

**Task:** Learn what a network and the Internet are, how devices are identified (IP vs MAC addresses), and how to test connectivity with ping and ICMP.

**Action:**

- Task 1, networks: a network is devices connected together so they can communicate.
- Task 2, the Internet: a network of networks, where private networks are joined through the public network. Background: ARPANET (late 1960s, US Defense Department funded) and the World Wide Web (Tim Berners-Lee, 1989).
- Task 3, identifying devices:
  - IP addresses are four octets. IPv4 allows 2^32 addresses and IPv6 allows 2^128. Addresses can be public or private.
  - MAC addresses are 12 hexadecimal characters assigned to the network interface by the manufacturer. They can be spoofed.
  - Lab: spoofed a MAC address to get past a MAC-filtered Wi-Fi portal, which shows why MAC filtering alone is weak security.
- Task 4, ping and ICMP: ping sends an ICMP echo request and receives an echo reply. Used `ping -c 4` against a public and a private address to see the difference in results.

**Result:** Completed the room.

**Key terms**

network, private vs public network, Internet, ARPANET, World Wide Web, IP address, IPv4, IPv6, octet, MAC address, MAC spoofing, ping, ICMP, echo request, echo reply
