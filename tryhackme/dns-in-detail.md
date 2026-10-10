# TryHackMe: DNS in Detail

Pre Security path, How The Web Works module. September 2026.

**Situation:** Final room of the How The Web Works module, covering how a domain name is resolved to an IP address.

**Task:** Understand what DNS does, how domains are structured, the common record types, and how a DNS request travels.

**Action:**

- Task 1, DNS maps human-readable names to IP addresses.
- Task 2, domain hierarchy: top-level domain (TLD, split into gTLD and ccTLD), second-level domain, and subdomain. Labels are at most 63 characters using a-z, 0-9, and hyphens (not at the start or end); a full domain is at most 253 characters.
- Task 3, record types: A (IPv4 address), AAAA (IPv6 address), CNAME (alias to another name), MX (mail servers, with priority), TXT (free text, used for SPF, DMARC, and ownership verification).
- Task 4, request flow: local cache, then the recursive DNS server (usually the ISP), then a root server, then the TLD server, then the authoritative server (nameserver). The answer is cached for its TTL.
- Task 5, practical: looked up several record types for a test domain with the room's lookup tool.

**Result:** Completed the room.

**Key terms**

DNS, TLD, gTLD, ccTLD, second-level domain, subdomain, A, AAAA, CNAME, MX, TXT, TTL, recursive DNS server, root server, authoritative server, nameserver, SPF, DMARC
