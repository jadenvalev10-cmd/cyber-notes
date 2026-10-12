# Security Incident Report: Redirected Web Traffic (tcpdump Analysis)

**Source:** Google Cybersecurity Certificate, Networks and Network Security (tcpdump activity)
**Evidence:** tcpdump traffic log supplied with the activity
**Note:** All domains and IP addresses are fictional course examples (IPs are in the reserved documentation ranges).

---

## Section 1: Network protocol involved

The protocol identified in the log is **HTTP** (Hypertext Transfer Protocol), seen on port 80 as `GET / HTTP/1.1` requests to `yummyrecipesforme.com` and `greatrecipesforme.com`.

| TCP/IP layer | Protocol observed |
|---|---|
| Application | HTTP (port 80), DNS (port 53) |
| Transport | TCP (SYN, SYN-ACK, ACK handshake visible) |
| Internet | IP |

DNS resolved both domain names before the HTTP connections were made.

## Section 2: Incident documentation

**Summary:** The log shows web traffic from an analyst machine (`your.machine`) to `yummyrecipesforme.com`, followed by traffic to a different domain, `greatrecipesforme.com`.

**Timeline**

| Time | Event |
|---|---|
| 14:18:32 | DNS A query for `yummyrecipesforme.com`; reply `203.0.113.22` |
| 14:18:36 | TCP handshake to port 80, then `GET / HTTP/1.1` |
| (log note) | Large volume of traffic on port 80 |
| 14:20:32 | DNS A query for `greatrecipesforme.com`; reply `192.0.2.17` |
| 14:25:29 | TCP handshake to port 80, then HTTP GET, then more port 80 traffic |

**Findings**

- The browser moved from the original site to a different domain and IP address within about seven minutes, which is not expected behavior for the original site.
- The traffic is unencrypted HTTP, so request and response content is readable in transit.
- The pattern is consistent with the site's content or code being altered after unauthorized access, such as a brute force attack on the administrator login.

**Limitations:** The log does not show login attempts. Brute force is an assessment to be confirmed against server authentication logs.

**Recommended follow-up:** Review the site source code and server login records, confirm whether the administrator account was accessed without authorization, and restore the site from a known good copy and reset credentials.

## Section 3: Recommended remediation

**Limit the number of login attempts (account lockout).** Configure the administrative login to lock the account, or block further attempts, after a small number of consecutive failures (for example, five), and alert the security team.

**Why it works:** Brute force attacks depend on submitting a very large number of password guesses quickly. A cap makes automated guessing impractical and creates a log record that analysts can monitor to detect an attack in progress. It works best alongside strong passwords and two-factor authentication.
