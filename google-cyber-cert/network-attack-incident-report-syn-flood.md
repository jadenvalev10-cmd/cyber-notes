# Cybersecurity Incident Report: Network Traffic Analysis (SYN Flood)

Google Cybersecurity Certificate activity

## Situation

A company's website was timing out for visitors. Acting as a security analyst, I was given a Wireshark capture of the traffic hitting the web server (192.0.2.1) and asked to identify what kind of network attack was occurring.

## Task

Find the pattern in the TCP/HTTP log, name the attack, and explain how it disrupts the website and what it costs the organization. I completed Sections 1 and 2 of the incident report template.

## Action

- Read the log and noticed most packets came from a single IP, 203.0.113.0: TCP SYN packets sent to the server's port 443, many per second, from the same source port, with no follow-up ACK.
- At the start of the log, legitimate visitors (198.51.100.x) completed the normal three-way handshake (SYN, SYN-ACK, ACK) and received HTTP 200 OK for /sales.html.
- Later, the server began answering real visitors with RST, ACK packets and HTTP 504 Gateway Time-out errors, matching the point where the flood became heavy.
- Concluded this was a DoS attack, not a DDoS, because all malicious traffic came from one source IP. A DDoS would come from many IPs at once.
- Section 1: named the attack, cited the log evidence, and tied it to the connection timeout symptom.
- Section 2: explained the three handshake steps, how unfinished handshakes leave half-open connections that consume server resources, and how that blocks legitimate users.
- Noted prevention measures: SYN cookies, firewall rate limiting of SYN requests, blocking the offending IP, an IDS/IPS, DDoS protection or a CDN, and alerting on SYN spikes.

## Result

Identified the attack as a SYN flood, a type of DoS attack. The website timed out because the attacker filled the server's connection queue with half-open connections, leaving no capacity for real customers. For the organization, the consequences are lost sales while the site is down, damaged customer trust, and staff time spent on incident response.

## Key terms

- **DoS (denial of service):** an attack, from one source, that makes a service unavailable to legitimate users.
- **DDoS (distributed denial of service):** the same goal, with attack traffic coming from many sources at once.
- **SYN flood:** a DoS attack that sends a large number of SYN packets and never completes the handshake.
- **Three-way handshake:** TCP connection setup, in the order SYN, SYN-ACK, ACK.
- **Half-open connection:** a connection where the server has answered a SYN but is still waiting for the final ACK.
- **RST:** the TCP flag that resets or refuses a connection.
- **504 Gateway Time-out:** the HTTP error returned when a server does not respond in time.
- **SYN cookies:** a defense that lets the server avoid holding resources for half-open connections.
