# TryHackMe: Packets & Frames

Pre Security path, Network Fundamentals module. September 2026.

**Situation:** Room on how data is broken into packets and frames and moved across a network, with two practicals.

**Task:** Learn the difference between packets and frames, TCP's three-way handshake, UDP's connectionless model, and ports.

**Action:**

- Task 1, packets vs frames: a packet works at Layer 3 (IP header plus payload); a frame works at Layer 2 (MAC addressing). Key IP header fields include TTL, checksum, and source and destination address.
- Task 2, TCP: connection-based, reliable, and slower than UDP. The three-way handshake is SYN, then SYN/ACK, then ACK. Connections close with FIN or RST.
- Task 3, practical: put the TCP handshake steps into the correct order.
- Task 4, UDP: stateless and connectionless, so faster, with simpler headers. Suited to loss-tolerant traffic such as streaming and voice.
- Task 5, ports: range 0-65535, with common ports in 0-1024. Standard ports: FTP 21, SSH 22, HTTP 80, HTTPS 443, SMB 445, RDP 3389. Practical: connect to a service on a chosen port.

**Result:** Completed the room.

**Key terms**

packet, frame, encapsulation, TCP, three-way handshake (SYN, SYN/ACK, ACK), sequence and acknowledgement numbers, FIN, RST, UDP, stateless, port, FTP, SSH, HTTP, HTTPS, SMB, RDP
