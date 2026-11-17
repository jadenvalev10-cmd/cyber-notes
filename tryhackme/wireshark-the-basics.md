# Wireshark: The Basics

Path: Cyber Security 101 > Networking

## Situation

Wireshark is an open-source, cross-platform packet analyser. It can sniff live traffic and inspect saved packet captures (PCAPs). This room covers the basics: finding my way around the interface, reading the OSI layers inside a packet, navigating a capture, and using display filters. I used two captures on the lab VM: http1.pcapng for the walkthrough and Exercise.pcapng for the questions.

## Task

Learn to navigate and configure Wireshark, read the TCP/IP layers of a packet, and apply display filters to narrow down traffic.

## Action

### Task 1 - Introduction

- Started the lab machine (split-screen view) and confirmed the two capture files on the VM.
- Noted that screenshots in the room use http1.pcapng, but the questions use Exercise.pcapng.

### Task 2 - Tool Overview

- Use cases: troubleshooting network problems (congestion, failure points), spotting security anomalies (rogue hosts, odd ports, suspicious traffic), and learning protocol details (response codes, payloads).
- Wireshark is NOT an IDS. It reads packets and does not modify them, so finding an anomaly depends on the analyst's knowledge.
- GUI sections: toolbar, display filter bar, recent files, capture filter and interfaces, status bar.
- Loaded a PCAP with File > Open, drag and drop, or double-clicking it in recent files.
- Three panes: Packet List (one-line summary per packet), Packet Details (protocol breakdown), Packet Bytes (hex plus ASCII; highlights the field I click).
- Colouring: default colours flag protocols and anomalies at a glance. Temporary rules last for the session (right-click or View > Conversation Filter). Permanent rules are saved in the profile (View > Coloring Rules). "Colourise Packet List" toggles colouring.
- Sniffing buttons: blue shark starts a capture, red stops it, green restarts it.
- Merge: File > Merge combines a second PCAP with the open one. The merged file has to be saved before working on it.
- Capture file details: Statistics > Capture File Properties (or the pcap icon bottom left) shows hash, capture time, comments, interface and statistics. Useful for identifying and prioritising files.
- Answered the questions by reading the capture file comments, packet count and file hash from the properties dialog.

### Task 3 - Packet Dissection

- Dissection means decoding a packet's protocols and fields. Packets have 5 to 7 layers based on OSI.
- Clicking a packet in the list shows its layers in the details pane (double-click opens a new window).
- The seven sections I saw:
  1. Frame: physical layer details, plus frame number and size.
  2. Source/Destination MAC: Data Link layer.
  3. Source/Destination IPv4: Network layer.
  4. Protocol (TCP/UDP): Transport layer, with ports.
  5. Protocol errors: continuation of layer 4, showing TCP segments that needed reassembly.
  6. Application protocol (HTTP, FTP, SMB): layer 5.
  7. Application data: extension of layer 5, with the app-specific content.
- Clicking any detail highlights the matching bytes in the bytes pane.
- Used these layers on a packet in Exercise.pcapng to pull out the markup language under HTTP, the arrival date, TTL, TCP payload size and an e-tag value.

### Task 4 - Packet Navigation

- Packet numbers: every packet gets a unique number, so I can jump back to a specific event. "Go" menu and toolbar allow go-to-packet and following a conversation.
- Find Packets (Edit > Find Packet): input types are Display filter, Hex, String and Regex. String and regex are most common. Searches are case insensitive unless I set otherwise. I also have to pick the pane to search (list, details or bytes), or it will miss content that lives in a different pane.
- Mark Packets: marked packets show black, and marks are lost when the file session closes.
- Packet Comments: unlike marks, they are saved inside the capture file until removed.
- Export Packets (File menu): pull out only the suspicious packets to share or dig into.
- Export Objects: extracts files transferred over DICOM, HTTP, IMF, SMB and TFTP.
- Time Display Format (View > Time Display Format): default is seconds since beginning of capture, and UTC is usually more useful.
- Expert Info (status bar or Analyse > Expert Information): flags protocol states. Severities: Chat (blue, normal workflow), Note (cyan, notable events), Warn (yellow, unusual codes or problems), Error (red, e.g. malformed packets). Groups include Checksum, Comment, Deprecated and Malformed. These are suggestions only, so false positives and negatives happen.
- Searched for a string in packet details, read a packet comment, used Export Objects to find a .txt file in the capture, and checked the expert info warning count.

### Task 5 - Packet Filtering

- Capture filters only capture matching packets. Display filters only change what is shown. (Capture vs display filters are covered in more depth in the next room.)
- Golden rule: "If you can click on it, you can filter and copy it."
- Apply as Filter: filters on the single field I clicked (right-click or Analyse > Apply as Filter). The status bar shows total vs displayed packets.
- Conversation Filter: shows only packets linked by the same IPs and ports, hiding the rest.
- Colourise Conversation: highlights the linked packets without filtering. Undo with View > Colourise Conversation > Reset Colourisation.
- Prepare as Filter: builds the query in the bar but waits for Enter, so I can chain it with and/or.
- Apply as Column: adds a field to the packet list as a column so I can see it across all packets.
- Follow Stream (right-click or Analyse > Follow TCP/UDP/HTTP Stream): rebuilds application-level data and can show unencrypted usernames, passwords and other data. Server packets show in blue, client in red. It auto-applies a filter, so I clear it with the X on the filter bar.
- Simple display filters: protocol name (http, arp, dhcp, ftp, smtp, pop, imap), tcp.port == 80 or udp.port == `<port>`, and ip.addr == `<IP>`.
- Applied HTTP as a filter from a packet, checked the displayed packet count, then followed an HTTP stream at a high packet number and read the server's response to count and name artists.

### Task 6 - Conclusion

- Recap only. Next room is Wireshark: Packet Operations.

## Result

I can open a capture, read each OSI layer in a packet, find and mark packets, export packets and objects, use Expert Info as a lead (not a verdict), and filter traffic by field, conversation, protocol, port or IP. Follow Stream was the most useful for investigations because it shows what was actually sent at the application layer.

## Key terms

- PCAP / PCAPNG: saved packet capture file
- Packet dissection: decoding a packet's protocols and fields
- Packet List / Details / Bytes panes: summary, protocol breakdown, hex+ASCII
- Display filter vs capture filter: filters what is shown vs what is captured
- Apply / Prepare as Filter: run a filter now vs build it first
- Conversation Filter vs Colourise Conversation: hide unrelated packets vs only highlight linked ones
- Follow Stream: reconstruct application-level data from packets
- Expert Info: Chat, Note, Warn, Error severity flags
- Export Objects: extract files from DICOM, HTTP, IMF, SMB, TFTP
- ip.addr == / tcp.port == / udp.port ==: basic display filter syntax
