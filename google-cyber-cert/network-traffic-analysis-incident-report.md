# Cybersecurity Incident Report: Network Traffic Analysis

*Google Cybersecurity Professional Certificate (Coursera) - network traffic analysis activity. The scenario and IP addresses are fictional.*

## Part 1: Summary of the problem found in the DNS and ICMP traffic log

The UDP protocol reveals that the request for the IP address of yummyrecipesforme.com was sent over UDP from the computer (192.51.100.15) to the DNS server (203.0.113.2) on port 53, and the packet could not be delivered.

This is based on the network analysis, which shows the ICMP echo reply returned the error message "udp port 53 unreachable." This shows the DNS server received the request but had no service listening on that port to answer it.

Port 53 is used for DNS (Domain Name System) traffic, which resolves domain names to IP addresses.

The most likely issue is that the DNS server is not listening on port 53. The DNS service may be down, or a firewall may be blocking port 53, so the domain name cannot be resolved and customers cannot reach the website.

## Part 2: Analysis of the data and likely cause of the incident

**Time incident occurred:** 1:24 p.m. (13:24:32), when the first DNS request in the tcpdump log was sent. The first ICMP error came back at 13:24:36.

**How the IT team became aware:** Several customers contacted the company to report that they could not access www.yummyrecipesforme.com and saw the error "destination port unreachable" after waiting for the page to load.

**Actions taken by the IT department:** The IT team tried to load the website and received the same "destination port unreachable" error. They then used tcpdump to capture network traffic while loading the page. The log showed the DNS queries sent over UDP being answered with ICMP error messages.

**Key findings:**

- The browser sent a UDP request (query ID 35084, A record) from 192.51.100.15 to the DNS server at 203.0.113.2 on port 53, asking for the IP address of yummyrecipesforme.com.
- The DNS server replied with an ICMP error: "udp port 53 unreachable." The same error was returned two more times on later attempts.
- No service was listening on port 53, so the domain name could not be resolved and the website could not load.

**Likely cause:** The DNS service on the DNS server (203.0.113.2) is most likely down or not listening on UDP port 53, or a firewall is blocking port 53. A denial of service (DoS) attack against the DNS server is also a possible cause.

**Next steps:**

1. Check whether the DNS service is running.
2. Review firewall rules for port 53.
3. Escalate to the security team to rule out an attack.

## Key terms

- **DNS:** system that resolves domain names to IP addresses (UDP port 53).
- **UDP:** connectionless transport protocol used for DNS queries.
- **ICMP:** protocol used to send error and diagnostic messages between devices.
- **tcpdump:** command-line packet capture and analysis tool.
- **DoS:** attack that overwhelms a service so legitimate users cannot reach it.
