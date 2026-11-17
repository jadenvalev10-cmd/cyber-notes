# Networking Concepts (Cyber Security 101 > Networking, Easy, 60 min, 8 tasks)

## Situation

This is the first of four rooms in the Networking module. It covers the two models used to describe how data moves across a network (ISO OSI and TCP/IP), how IP addressing and transport protocols work, and how to connect to an open TCP port from the command line. I needed this to understand terms like “layer 3 switch” and “layer 7 firewall” and to read network traffic later.

## Task

Learn the OSI and TCP/IP layers, IP addressing and subnets, UDP vs TCP, and encapsulation. Then use Telnet to connect to services on a target machine.

## Action

- Task 1 (Introduction): Read the learning objectives and the room series order: Networking Concepts, Networking Essentials, Networking Core Protocols, Networking Secure Protocols.
- Task 2 (OSI Model): Learned the seven layers from bottom to top, with the mnemonic “Please Do Not Throw Spinach Pizza Away.”
  - Layer 1, Physical: the medium and the 0s and 1s, sent as electrical, optical, or wireless signals (Ethernet cable, fibre, WiFi bands 2.4, 5, and 6 GHz).
  - Layer 2, Data Link: communication between nodes on the same network segment (Ethernet 802.3, WiFi 802.11). It uses 6-byte MAC addresses written in hex, where the first 3 bytes identify the vendor. Each frame carries a destination and a source MAC.
  - Layer 3, Network: logical addressing and routing between different networks (IP, ICMP, IPSec).
  - Layer 4, Transport: end-to-end communication between applications on different hosts, including flow control, segmentation, and error correction (TCP, UDP).
  - Layer 5, Session: establishing, maintaining, and synchronising sessions, with recovery if a transfer fails (NFS, RPC).
  - Layer 6, Presentation: encoding, compression, and encryption so the application can read the data (ASCII/Unicode, JPEG/PNG, MIME).
  - Layer 7, Application: network services for end-user apps (HTTP, FTP, DNS, POP3, SMTP, IMAP).
- Task 3 (TCP/IP Model): Learned that TCP/IP is the implemented model (RFC 1122, from the 1970s). It has four layers:
  - Application: covers OSI layers 5, 6, and 7.
  - Transport: OSI layer 4.
  - Internet: OSI layer 3.
  - Link: OSI layer 2.
  - RFC 1122 has no separate physical layer, so many textbooks show a five-layer version instead.
- Task 4 (IP Addresses and Subnets):
  - An IPv4 address is 4 octets (32 bits), each octet 0-255. It uniquely identifies a host, like a postal address.
  - In a /24 network such as 192.168.1.x, .0 is the network address and .255 is the broadcast address.
  - A subnet is a smaller network inside a bigger one. The subnet mask 255.255.255.0 is the same as /24, meaning the leftmost 24 bits are the network part.
  - Checked my own config with ipconfig (Windows) and ifconfig or ip a s (Linux) to find the IP, mask, and broadcast address.
  - Private ranges from RFC 1918: 10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16. Anything else is public.
  - Routers forward packets between networks, like a post office deciding where a parcel goes next.
  - Used the ranges above to spot which sample addresses were not private, and which were not valid because an octet was over 255.
- Task 5 (UDP and TCP):
  - UDP is simple and connectionless, with no delivery confirmation, like regular mail. It uses source and destination port numbers to reach a specific process on a host.
  - Ports are 16-bit, so the range is 1 to 65,535 (roughly 65 thousand).
  - TCP is connection-oriented and acknowledges data. Every byte has a sequence number, so the receiver can spot lost or out-of-order data.
  - TCP connects with a three-way handshake: SYN from the client, SYN-ACK from the server, ACK from the client.
  - TCP uses port numbers like UDP to identify processes.
- Task 6 (Encapsulation):
  - Each layer wraps the data from the layer above with its own header (and a trailer at the link layer). This lets each layer focus on its own job.
  - Application data becomes a TCP segment or UDP datagram at the transport layer, then an IP packet at the network layer, then a frame at the data link layer.
  - The receiver reverses the process until the application data comes out.
  - Walked through the “life of a packet” for a web search: HTTPS request, TCP handshake, IP adds source and destination IPs, link layer adds MACs, and each router strips and rebuilds the link layer header while forwarding.
- Task 7 (Telnet):
  - Deployed the target machine and the AttackBox, then connected to services with telnet MACHINE_IP PORT.
  - Telnet is a remote terminal protocol that sends everything, including passwords, in clear text, which is why SSH replaced it.
  - Echo server (port 7): connected and confirmed it repeats back whatever I type.
  - Daytime server (port 13): connected and it returned the current date and time.
  - Web server (port 80): sent a manual HTTP request: GET / HTTP/1.1, then Host: telnet.thm, then a blank line to finish the request. The Host: header is required because one server can host many sites on one IP.
  - Read the HTTP response headers, including the server software and version. The server closed the connection after responding.
  - Exited a session with Ctrl+] then quit.
- Task 8 (Conclusion): Reviewed the concepts covered and noted that the next room is Networking Essentials.

## Result

Completed the room at 100%. I can name all seven OSI layers with their functions and example protocols, map them to the four TCP/IP layers, and explain how encapsulation turns data into segments, packets, and frames. I can identify private vs public IPs and invalid IPs, and explain UDP vs TCP including the handshake. I also used Telnet to talk to a service directly and make a raw HTTP request, which showed that web traffic is just text over TCP port 80.

## Key terms

OSI model, TCP/IP model, network segment, MAC address, frame, packet, segment, datagram, encapsulation, IP address, octet, subnet, subnet mask, CIDR (/24), broadcast address, private IP (RFC 1918), router, port number, UDP, TCP, three-way handshake (SYN, SYN-ACK, ACK), sequence number, Telnet, clear text, Host header.
