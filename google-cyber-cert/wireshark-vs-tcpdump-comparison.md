# Wireshark vs. tcpdump: Comparing Network Protocol Analyzers

Google Cybersecurity Certificate activity

## Situation

As a cybersecurity analyst, I was asked to research how two network protocol analyzers, Wireshark and tcpdump, are alike and different. A network protocol analyzer (also called a packet sniffer) captures and analyzes the traffic on a network so analysts can see how data is flowing.

## Task

Research both tools and fill out a Venn diagram with at least two differences for each tool and at least three similarities.

## Action

- **Research:** I read the official Wireshark and tcpdump documentation and compared the tools on what you need to run them, the interface, how analysts use them, how they capture, analyze, and filter traffic, and their limitations.
- **Wireshark:** It has a graphical interface (GUI) with color-coded packets and a three-pane view (packet list, packet details, packet bytes). It does deep analysis with protocol dissectors, display filters, and Follow TCP Stream. It works best for detailed analysis of saved captures on a desktop.
- **tcpdump:** It is command-line only and prints lightweight text output. It runs on headless servers over SSH, so it is good for quick captures and troubleshooting. Filters are set with command-line options and BPF expressions.
- **Similarities:** Both are free and open source, both capture live traffic and read and save .pcap files, and both filter by protocol, IP address, and port.
- **Template:** I filled in the Venn diagram and saved a blank copy of the template to reuse later.

## Result

I completed the Venn diagram with three points for each tool and three similarities. The takeaway is that the two tools work well together: tcpdump is the quick way to capture traffic on a server with no GUI, and Wireshark is where I can open that .pcap file and dig into it.

## Key terms

- **Network protocol analyzer (packet sniffer):** a tool that captures and analyzes network traffic.
- **.pcap:** the packet capture file format that both tools can read and write.
- **BPF (Berkeley Packet Filter):** the filter syntax tcpdump uses to choose which packets to capture.
- **Display filter:** Wireshark's filter for narrowing down which packets are shown in a capture.
- **GUI vs. CLI:** a graphical interface vs. a command-line interface.
- **Headless server:** a server with no graphical desktop.
