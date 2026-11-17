# Networking Secure Protocols**

** Path: Cyber Security 101 > Networking (room 4 of 4) | Difficulty: Easy

## Situation

The protocols from the previous room (HTTP, SMTP, POP3, IMAP, Telnet) send data in cleartext. That means they don’t protect confidentiality (someone sniffing can read passwords), integrity (an attacker can change the data in transit), or authenticity (you can’t be sure the server is the real one). This room covers the three main ways to fix that: TLS, SSH, and VPNs.

## Task

Learn how TLS secures existing protocols, how SSH replaced Telnet, how SFTP and FTPS secure file transfer, and how a VPN protects traffic across an untrusted network. Finish by decrypting captured TLS traffic in Wireshark and finding the login credentials in it.

## Action

- Task 1 (Introduction): I reviewed why cleartext protocols are a risk. The three goals are confidentiality, integrity, and authenticity. Adding TLS turns HTTP, POP3, SMTP, and IMAP into HTTPS, POP3S, SMTPS, and IMAPS.
- Task 2 (TLS):
  - Before TLS, an attacker could put a network card in promiscuous mode and read everyone’s credentials from the packet captures.
  - Netscape built SSL (SSL 2.0 in 1995). The IETF developed TLS in 1999, and TLS 1.0 was an upgrade to SSL 3.0.
  - TLS is a cryptographic protocol that works at the transport layer and guarantees confidentiality and integrity. Other protocols have been upgraded with it too, such as DNS to DoT, MQTT to MQTTS, and SIP to SIPS.
  - To identify itself, a server creates a Certificate Signing Request (CSR) and sends it to a Certificate Authority (CA). The CA verifies it and issues a signed digital certificate. A host trusts that certificate only if the CA’s certificate is installed on it.
  - Certificates normally cost money to get signed, but Let’s Encrypt signs them for free.
  - A self-signed certificate can’t prove a server’s authenticity, because no third party has confirmed it.
- Task 3 (HTTPS):
  - Plain HTTP runs on TCP port 80. A page request is a TCP three-way handshake followed by HTTP, such as GET / HTTP/1.1.
  - HTTPS is HTTP over TLS on port 443. The request becomes a TCP handshake, then TLS negotiation, then HTTP.
  - In Wireshark, the HTTP data shows up as “Application Data”, and following the stream gives only gibberish.
  - Once I supplied the key, the same traffic decrypted into normal HTTP. The takeaway is that TLS secured HTTP without changing TCP, IP, or HTTP itself.
- Task 4 (SMTPS, POP3S, IMAPS): Adding TLS to these works the same way as for HTTPS. I compared the default ports (table in Key terms).
- Task 5 (SSH):
  - Telnet sends everything in cleartext, including credentials. Tatu Ylönen released SSH-1 in 1995 and SSH-2 followed in 1996. OpenBSD released OpenSSH in 1999, and most SSH clients today are built on it.
  - Benefits:
    - Secure authentication, including passwords, public keys, and two-factor.
    - End-to-end encryption, with warnings about new server keys to protect against man-in-the-middle attacks.
    - Integrity protection for the traffic.
    - Tunneling other protocols through SSH, which gives a VPN-like connection.
    - X11 forwarding for graphical apps.
  - I connect with ssh username@hostname, or ssh hostname if the username matches mine. I add -X to run graphical programs remotely. The SSH server listens on port 22, where Telnet uses 23.
- Task 6 (SFTP and FTPS):
  - SFTP is the SSH File Transfer Protocol. It’s part of the SSH suite and shares port 22. I connect with sftp username@hostname and use get filename and put filename to download and upload.
  - FTPS is FTP secured with TLS, so it needs a proper certificate. It uses port 990 where FTP uses 21. It’s awkward through strict firewalls because it uses separate control and data connections.
  - I completed the hands-on matching exercise, pairing each cleartext protocol with its secure port.
- Task 7 (VPN):
  - A VPN’s “Virtual” part means it runs over normal Internet infrastructure, which is cheap. The “Private” part means encrypting the data, because TCP/IP has no built-in protection against disclosure or alteration.
  - A VPN client encrypts traffic and sends it through a tunnel to the VPN server. This can connect remote branches or individual remote users to a main site.
  - Normally all my Internet traffic goes through the tunnel. Websites see the VPN server’s IP, not mine, and my ISP sees only encrypted traffic.
  - Some VPNs don’t route all traffic, and some leak the real IP, so I might need a DNS leak test.
  - VPNs are illegal in some countries, so I should check local laws.
- Task 8 (Closing Notes, hands-on challenge):
  - I used a lab machine with Chromium set to log TLS session keys (chromium --ssl-key-log-file=~/ssl-key.log).
  - In Wireshark, I opened randy-chromium.pcapng. Then I right-clicked a TLS packet, went to Protocol Preferences, then Transport Layer Security, then Open Transport Layer Security preferences. I browsed to the key log file as the (Pre)-Master-Secret log and clicked OK.
  - The TLS traffic decrypted and I found the submitted credentials inside the HTTP form data.

## Finding credentials in decrypted traffic

The room doesn’t say which packet holds the login, so I had to narrow the capture down myself.

- Protocol name: after decryption, most packets show as HTTP2. That’s just the version of HTTP browsers use over TLS, and it isn’t suspicious by itself.
- What to look for: a DATA frame going from the client to the server with the content type application/x-www-form-urlencoded in the Info column. That’s how a browser sends HTML form fields as key=value pairs, and login forms use it.
- Check the direction: the source should be the machine running the browser. A client-to-server body means something is being submitted. Most traffic is the client asking for pages or the server answering.
- Methods to find it:
  - Filter by content type with the display filter urlencoded-form.
  - Search with Ctrl+F, set to “String” in “Packet details”, for terms like pass, password, or login.
  - Filter on the POST method, since credentials are sent in a POST rather than a GET.
  - Right-click a suspicious packet and use Follow, then HTTP/2 Stream, to read the whole request.
- Confirming it: expand the packet’s HTML Form URL Encoded section and read the field names, such as an email and a password.
- Without the key log loaded, none of this works, because everything shows only as “Application Data”.

## Result

I completed the room (8/8 tasks). I now understand the three ways to secure traffic: TLS for protocols like HTTP, SMTP, POP3, and IMAP; SSH for remote access, file transfer, and tunnels; and VPNs for connecting sites or users securely. I also learned how to decrypt TLS in Wireshark with a session key log, and how to pick the login out of the decrypted traffic by filtering for client-to-server form submissions.

## Key terms

- TLS / SSL: the encryption layer added to other protocols. TLS is the newer version, and SSL is the older one.
- CSR / CA / self-signed certificate: the request for a certificate, the authority that signs it, and a certificate nobody has verified.
- Let’s Encrypt: a free CA.
- SSH / OpenSSH: Secure Shell and its open-source implementation.
- SFTP vs FTPS: SFTP is file transfer over SSH, and FTPS is FTP over TLS. They are different things.
- VPN tunnel: the encrypted path between a VPN client and a VPN server.
- TLS key log (ssl-key.log): the file of session keys the browser writes, which Wireshark uses to decrypt TLS.
- application/x-www-form-urlencoded: the content type browsers use to send form fields as key=value pairs.
- Ports, cleartext to secure:

|  |  |  |
| :-: | :-: | :-: |
| **Protocol** | **Cleartext** | **Secure** |
| HTTP | 80 | HTTPS 443 |
| SMTP | 25 | SMTPS 465 and 587 |
| POP3 | 110 | POP3S 995 |
| IMAP | 143 | IMAPS 993 |
| Telnet | 23 | SSH 22 |
| FTP | 21 | FTPS 990 (SFTP uses 22) |
