# cyber-notes

Study notes and write-ups from my path into cybersecurity: hands-on TryHackMe rooms and activities from the Google Cybersecurity Professional Certificate.

I'm a computer science student building toward a career in cybersecurity. This repo tracks what I've learned, room by room and activity by activity. Most entries follow STAR format (Situation, Task, Action, Result).

## Google Cybersecurity Certificate

| Activity | What it covers |
| :-- | :-- |
| [Botium Toys: Controls and Compliance Checklist](google-cyber-cert/botium-toys-controls-compliance-checklist.md) | Internal security audit: controls assessment, PCI DSS / GDPR / SOC compliance review, and prioritized risk recommendations |
| [Network Traffic Analysis: Incident Report](google-cyber-cert/network-traffic-analysis-incident-report.md) | Incident report on a DNS/ICMP tcpdump log: "udp port 53 unreachable" error, likely causes, and next steps |
| [Network Attack Incident Report: SYN Flood](google-cyber-cert/network-attack-incident-report-syn-flood.md) | Incident report on a Wireshark TCP/HTTP log: identifying a single-source SYN flood (DoS), how it exhausts the server and causes timeouts, and prevention measures |
| [Security Incident Report: Redirected Web Traffic](google-cyber-cert/security-incident-report-brute-force.md) | Incident report on a tcpdump log: HTTP over TCP/IP layers, DNS lookups and a redirect to a second domain, and account lockout as a brute force remediation |

## TryHackMe

| Room | What it covers |
| :-- | :-- |
| [Computer Types](tryhackme/computer-types.md) | Direct-use vs. behind-the-scenes computers: servers, IoT, embedded systems |
| [Client-Server Basics](tryhackme/client-server-basics.md) | Client-server model, ports, protocols, DNS, HTTP requests in browser dev tools |
| [Virtualisation Basics](tryhackme/virtualisation-basics.md) | Hypervisors, VM isolation, and why it matters for security |
| [Operating Systems: Introduction](tryhackme/operating-systems-introduction.md) | Kernel space vs. user space, GUI vs. CLI |
| [Linux CLI Basics](tryhackme/linux-cli-basics.md) | Navigating and searching a Linux filesystem, system recon commands |
| [Windows CLI Basics](tryhackme/windows-cli-basics.md) | Command Prompt navigation, file search, system and network recon |
| [Data Encoding](tryhackme/data-encoding.md) | ASCII, ISO-8859, Unicode, UTF-8/16/32 |
| [Python: Simple Demo](tryhackme/python-simple-demo.md) | Variables, conditionals, and loops via a number-guessing game |
| [JavaScript: Simple Demo](tryhackme/javascript-simple-demo.md) | Variables, conditionals, and loops in a JavaScript game, compared with the Python version |
| [Database SQL Basics](tryhackme/database-sql-basics.md) | Tables, rows, and columns, and querying data with SELECT, FROM, WHERE, and ORDER BY |
| [What is Networking?](tryhackme/what-is-networking.md) | Networks and the Internet, IP vs MAC addresses, MAC spoofing, ping and ICMP |
| [Intro to LAN](tryhackme/intro-to-lan.md) | Star, bus, and ring topologies, switches vs routers, subnetting, ARP, and DHCP |
| [OSI Model](tryhackme/osi-model.md) | The seven OSI layers, their roles, and key protocols such as TCP, UDP, OSPF, and DNS |
| [Packets & Frames](tryhackme/packets-and-frames.md) | Packets vs frames, TCP three-way handshake, UDP, and common ports |
| [Extending Your Network](tryhackme/extending-your-network.md) | Port forwarding, stateful vs stateless firewalls, VPNs, switches, routers, and VLANs |
| [DNS in Detail](tryhackme/dns-in-detail.md) | Domain hierarchy, DNS record types (A, AAAA, CNAME, MX, TXT), and how a DNS request is resolved |
| [HTTP in Detail](tryhackme/http-in-detail.md) | URLs, requests and responses, methods, status codes, headers, and cookies |
| [How Websites Work](tryhackme/how-websites-work.md) | HTML and JavaScript on the front end, sensitive data exposure, and HTML injection |
| [The CIA Triad](tryhackme/the-cia-triad.md) | Confidentiality, integrity, and availability, and classifying security incidents by pillar |
| [Cryptography Concepts](tryhackme/cryptography-concepts.md) | Plaintext, ciphertext, and keys, symmetric vs asymmetric encryption, and hybrid use in HTTPS |
| [Become a Hacker](tryhackme/become-a-hacker.md) | Offensive security basics, the ethical hacker role, enumeration, and dictionary attacks |

Room answers and flag values are intentionally left out.
