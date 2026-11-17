# Networking Core Protocols

Path: Cyber Security 101 > Networking (room 3 of 4)

## Situation

This room is the third in the networking series, after Networking Concepts and Networking Essentials. Up to now I had learned the OSI and TCP/IP models and how Ethernet, IP and TCP work. This room covers the application-layer protocols that sit on top of them: DNS, WHOIS, HTTP(S), FTP, SMTP, POP3 and IMAP. Most of them are plain-text protocols, so I could talk to the servers by hand with telnet and the ftp client and watch the packets in Wireshark/tshark.

## Task

Learn what each core protocol does, what its default port is, and what its main commands look like. Then use telnet and an FTP client against the lab machine to see how these protocols work behind the graphical programs I normally use.

## Action

### Task 1: Introduction

- Started the AttackBox and the lab machine. Learning objectives were WHOIS, DNS, HTTP, FTP, SMTP, POP3 and IMAP.

### Task 2: DNS

- DNS maps a domain name to an IP address so nobody has to memorize IPs. It works at Layer 7 (Application). It uses UDP port 53 by default and falls back to TCP port 53.
- Record types I covered:
  - A record: hostname to one or more IPv4 addresses.
  - AAAA record: hostname to IPv6 addresses (quad-A).
  - CNAME record: maps one domain name to another domain name.
  - MX record: names the mail server that handles email for a domain.
- Typing a site into a browser makes it ask DNS for the A record. Sending an email makes the mail server ask for the MX record.
- Used nslookup to look up a domain from the command line. It returned an IPv4 and an IPv6 address.
- Read a tshark capture of that lookup. It was four packets: an A query and its response, then an AAAA query and its response.

### Task 3: WHOIS

- Whoever registers a domain is allowed to set its DNS records. Registration is paid yearly and needs accurate contact info for the registrant.
- That info is public through WHOIS records. WHOIS is not an acronym, it is pronounced “who is”.
- Privacy services can replace the registrant’s details with the proxy company’s, so the real owner is hidden.
- Used the whois command on Linux (and the idea of online lookups) to read a record. A record shows registrar, creation date, last updated date, expiry date, and registrant name, org, address, phone and email (or the privacy proxy’s info).
- Looked up the creation dates of two well-known domains.

### Task 4: HTTP(S)

- HTTP is how the browser talks to web servers. It runs over TCP. HTTPS is the secure version.
- Main methods:
  - GET: retrieve data (a page, an image)
  - POST: submit new data (a form, an upload)
  - PUT: create a resource or overwrite an existing one
  - DELETE: delete a resource
- Default ports: 80 for HTTP and 443 for HTTPS. Less common ones are 8080 and 8443.
- Wireshark showed a lot of information exchanged that the browser never displays, like the web server version and when the page was last modified.
- Used telnet to talk HTTP by hand: connect to port 80, then send GET / HTTP/1.1 and a Host: header. To get a specific file, send GET /file.html HTTP/1.1. Good for troubleshooting.
- Used this to pull a specific page off the lab web server.

### Task 5: FTP

- FTP is built for transferring files and can be faster than HTTP for that. Commands:
  - USER and PASS: log in
  - RETR: download a file from server to client
  - STOR: upload a file from client to server
- The server listens on TCP port 21. The actual data (directory listings and files) goes over a separate connection from the client to the server.
- Connected with the ftp client, logged in as anonymous (no password needed), ran ls, switched with type ascii, and downloaded files with get. Quit to disconnect.
- In Wireshark, typing ls on the client sends LIST to the server, so client commands and protocol commands are not always the same word.
- Retrieved the flag file from the lab FTP server.

### Task 6: SMTP

- SMTP sends email, both from a mail client to a server and from one mail server to another. Like handing a package to the post office.
- Commands, in order:
  - HELO or EHLO: start the session
  - MAIL FROM: sender address
  - RCPT TO: recipient address
  - DATA: the message contents are coming
  - a single “.” on a line by itself: end of the message
- Default port is TCP 25.
- Sent an email over telnet to port 25 by typing each command myself. Cumbersome, but it shows exactly what an email client does under the hood.

### Task 7: POP3

- POP3 retrieves email from a server to a local client (SMTP sends, POP3 receives). Like checking a mailbox for letters.
- Commands:
  - USER and PASS: log in
  - STAT: number of messages and total size
  - LIST: list messages and sizes
  - RETR n: retrieve message n
  - DELE n: mark message n for deletion
  - QUIT: end the session and apply changes like deletions
- Default port is TCP 110.
- Connected with telnet to port 110, logged in, and used STAT, LIST and RETR to read messages, including the one I sent over SMTP.
- In the capture, anyone sniffing the traffic could read the username and password in clear text.
- Noted the server software name from the greeting banner.

### Task 8: IMAP

- IMAP keeps a mailbox in sync across multiple devices. Read, moved and deleted states sync. Unlike POP3, mail stays on the server, so it uses more server storage.
- Commands are more complex than POP3 and each one starts with a tag (like A, B, C):
  - LOGIN user pass: authenticate
  - SELECT mailbox: pick a folder to work in
  - FETCH n body[]: get header and body of message n
  - MOVE and COPY: move or copy messages to another mailbox
  - LOGOUT: end the session
- Default port is TCP 143.
- Connected with telnet to port 143, logged in, selected the inbox (the server reports how many messages exist and which is the first unseen), and fetched a message.

### Task 9: Conclusion

- Reviewed the default port table (below). The room’s main point was understanding how a protocol works behind the graphical interface.

## Result

I finished all nine tasks. I can now describe what each of these protocols does and recognize its default port and main commands. I also got hands-on practice speaking HTTP, FTP, SMTP, POP3 and IMAP by hand over telnet and the ftp client, and I saw in Wireshark that FTP, POP3 and the others send credentials and content in clear text. That sets up the next room, Networking Secure Protocols, which covers securing these.

## Key terms and ports

- DNS: UDP 53 (TCP 53 fallback); records A, AAAA, CNAME, MX
- WHOIS: public domain registration records; privacy services hide registrant info
- HTTP: TCP 80; HTTPS: TCP 443; also 8080 and 8443; methods GET, POST, PUT, DELETE
- FTP: TCP 21 for control, separate connection for data; USER, PASS, RETR, STOR
- SMTP: TCP 25; HELO/EHLO, MAIL FROM, RCPT TO, DATA, “.”
- POP3: TCP 110; USER, PASS, STAT, LIST, RETR, DELE, QUIT
- IMAP: TCP 143; LOGIN, SELECT, FETCH, MOVE, COPY, LOGOUT
- TELNET: TCP 23 (from the previous room)
- Tools: nslookup, whois, tshark, Wireshark, telnet, ftp
