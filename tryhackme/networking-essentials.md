# Networking Essentials

Path: Cyber Security 101 > Networking (room 2 of 4) | Easy | ~60 min | 7 tasks

## Situation

After Networking Concepts (OSI, TCP/IP, IP addressing, TCP/UDP), I needed to understand the protocols that make a network work day to day: how a device gets its settings automatically, how it finds other devices on the local network, how connectivity is tested, how packets cross the Internet, and how many private devices share one public IP.

## Task

Learn and explain DHCP, ARP, ICMP (ping and traceroute), routing protocols, and NAT, and read the packet captures that show each one in action.

## Action

### Task 1: Introduction

- Confirmed the prerequisites: OSI and TCP/IP layers, plus Ethernet, IP, and TCP.
- Noted that this is room 2 of 4 (Networking Concepts, Networking Essentials, Networking Core Protocols, Networking Secure Protocols).

### Task 2: DHCP

- A device needs three things to use a network: an IP address with subnet mask, a router (gateway), and a DNS server.
- Manual configuration suits servers, since they don't change networks and other devices expect them at fixed addresses. Automatic configuration suits everything else.
- DHCP (Dynamic Host Configuration Protocol) is an application-layer protocol that runs over UDP. The server listens on UDP port 67 and the client sends from UDP port 68.
- Automatic configuration saves manual setup (important for mobile devices) and avoids IP address conflicts, where two hosts with the same IP can't use the network properly.
- DHCP follows four steps, DORA:
  - Discover: the client broadcasts DHCPDISCOVER looking for a server.
  - Offer: the server replies with DHCPOFFER, proposing an available IP.
  - Request: the client sends DHCPREQUEST to accept the offered IP.
  - Acknowledge: the server sends DHCPACK to confirm the assignment.
- Read a tshark capture of a DORA exchange (tshark -r file.pcap -n). The client ended up with 192.168.66.133.
- Discover and Request come from 0.0.0.0 to the broadcast IP 255.255.255.255, because the client has no IP configuration yet. At the link layer they go to the broadcast MAC ff:ff:ff:ff:ff:ff.
- The Offer and ACK come from the server (192.168.66.1) and are sent to the client's MAC address.
- At the end the client has a leased IP, a gateway to route packets outside the local network, and a DNS server to resolve domain names.

### Task 3: ARP

- IP packets travel inside data link frames (Ethernet 802.3 or WiFi 802.11). To build the frame header you need the target's MAC address, even though you only know its IP.
- A MAC address is 48 bits, written in hex (e.g. 7C:DF:A1:D3:8C:5C).
- DHCP gives a device the IP of the gateway and DNS server, but not their MACs. Devices on the same Ethernet only need each other's MACs while communicating.
- The Ethernet frame header holds destination MAC, source MAC, and type (IPv4 in this case).
- ARP (Address Resolution Protocol) finds the MAC address that belongs to an IP address on the same network.
- ARP Request: a broadcast to ff:ff:ff:ff:ff:ff asking "who has 192.168.66.1? tell 192.168.66.89".
- ARP Reply: the owner answers "192.168.66.1 is at `<its MAC>`". After that the two hosts can exchange frames.
- tshark shows "Who has... / ... is at...". tcpdump (tcpdump -r file -n -v) uses the terms Request who-has and Reply is-at.
- ARP is not wrapped in UDP or IP. It sits directly inside an Ethernet frame.
- Some call ARP layer 2 (it deals with MACs), others layer 3 (it supports IP). What matters is that it translates layer 3 addresses to layer 2 addresses.

### Task 4: ICMP

- ICMP (Internet Control Message Protocol) is used for network diagnostics and error reporting. Two commands rely on it: ping and traceroute (tracert on Windows).
- ping: sends an ICMP Echo Request (Type 8) and expects an Echo Reply (Type 0). It tests whether a target is alive and measures round-trip time (RTT).
- No reply doesn't always mean the host is down. A firewall on the path can block the packets.
- Used ping IP -c 4 to send four packets. The output shows packet loss and RTT min/avg/max/mdev.
- Packet sizes: Linux ping sends 56 bytes of data by default, plus an 8-byte ICMP header (64 bytes) plus a 20-byte IP header (84 bytes total), which is why it reads 56(84). Windows defaults to 32 bytes. Always read the Data field of the specific capture.
- traceroute: uses the IP Time-to-Live (TTL) field, which is the maximum number of routers a packet may pass through. Each router subtracts 1; at 0 the router drops the packet and sends back ICMP Time Exceeded (Type 11).
- It sends a probe with TTL 1 (first router replies and reveals itself), then TTL 2, and so on until the target is reached. Each responding router becomes one line of output.
- Some routers don't respond (shown as `* * *`), some reveal private ISP addresses, some reveal public IPs I could look up. The route can change between runs.
- Read the example traceroute to example.com: gateway first, private ranges, silent hops, then ISP and backbone routers, ending at the target.

### Task 5: Routing

- Routing is how a packet finds its way across millions of routers. There are many possible paths, so each router needs an algorithm to pick the right link.
- Routing algorithms are out of scope, but I learned the protocol names:
  - OSPF (Open Shortest Path First): routers share link state and each builds a full map of the network to compute the most efficient paths.
  - EIGRP (Enhanced Interior Gateway Routing Protocol): Cisco proprietary; routers share reachable networks and a cost (bandwidth, delay).
  - BGP (Border Gateway Protocol): the main routing protocol of the Internet; networks such as ISPs exchange routing information with each other.
  - RIP (Routing Information Protocol): simple, for small networks; picks the route with the fewest hops.

### Task 6: NAT

- IPv4 supports about 4 billion addresses, which isn't enough for all devices. NAT (Network Address Translation) is one fix: one public IP serves many private IPs.
- Unlike plain routing, a NAT router has to track connections, so it keeps a translation table mapping internal IP:port to external IP:port.
- Example from the diagram: a laptop at 192.168.0.129 using TCP source port 15401 appears to the web server as 212.3.4.5 with port 19273. The router handles it seamlessly.
- Many private devices sharing one public address by using different ports is technically PAT (Port Address Translation), also called NAT overload. Plain NAT swaps one private address for one public address and leaves ports alone. Home routers do the port-based version but everyone still calls it NAT.
- Ports are 16-bit, so one public IP has about 65,535 usable ports. Each tracked connection needs its own translated port, which caps one public IP at roughly 65 thousand simultaneous connections.

### Task 7: Closing Notes

- Recapped DHCP, ARP, ICMP, NAT, and routing, and completed the short interactive site to finish the room.

## Result

I can now follow how a device joins a network end to end: DHCP gives it an IP, gateway, and DNS server; ARP resolves the MAC addresses of its neighbours; ping and traceroute (ICMP) test and map the path; routing protocols decide how packets cross networks; and NAT lets a whole network share one public IP. I can also read the matching tshark and tcpdump output. Next room: Networking Core Protocols.

## Key terms

DHCP, DORA (Discover/Offer/Request/Acknowledge), UDP 67/68, 0.0.0.0, 255.255.255.255, ff:ff:ff:ff:ff:ff, ARP Request/Reply, tshark, tcpdump, ICMP, Echo Request (Type 8), Echo Reply (Type 0), Time Exceeded (Type 11), RTT, ping, traceroute/tracert, TTL, OSPF, EIGRP, BGP, RIP, NAT, PAT/NAT overload, translation table, 16-bit port (65,535)
