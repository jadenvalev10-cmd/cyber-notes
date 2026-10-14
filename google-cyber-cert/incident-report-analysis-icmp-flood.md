# Incident Report Analysis: ICMP Flood (DoS)

Google Cybersecurity Certificate activity. I used the NIST Cybersecurity Framework (CSF) to write up a network incident.

## Situation

I played a cybersecurity analyst at a small multimedia company that does web design, graphic design, and social media marketing for small businesses. The company's internal network went down for two hours because someone flooded it with ICMP packets (a ping flood). Nothing on the internal network could reach its resources while it lasted.

The incident team blocked incoming ICMP, took the non-critical services offline, and brought the critical ones back up. The investigation showed the attacker got in through a firewall that had never been configured, so nothing was filtering or limiting the ICMP traffic. That made it a denial of service (DoS) attack.

After the incident, the network security team added:

1. A firewall rule that limits how many ICMP packets can come in.
2. Source IP address verification on the firewall, to catch spoofed addresses.
3. Network monitoring software to spot unusual traffic.
4. An IDS/IPS that filters ICMP traffic that looks suspicious.

## Task

Use the NIST CSF to analyze the incident and build a plan for improving the company's network security. I filled out the incident report template with a summary and a section for each CSF function: Identify, Protect, Detect, Respond, and Recover.

## Action

**Summary:** The network was down for two hours from an ICMP flood that came in through an unconfigured firewall. Blocking ICMP, taking non-critical services offline, and adding new controls got things back to normal.

**Identify**

- Attack type: DoS, specifically an ICMP flood (ping flood). The source IPs may have been spoofed.
- Affected: the whole internal network and everything that depends on it. The firewall was the weak point.
- Cause: no firewall rule to filter or limit ICMP, and no check on source IPs.
- Impact: about two hours of downtime.
- Next step: audit every firewall, network device, and set of access privileges for gaps like this one.

**Protect**

- Already done: the ICMP rate limit and the source IP check.
- Still to do: review each firewall and router against a documented baseline on a regular schedule, keep rules and firmware updated, and only allow the ICMP types the business actually needs.
- Limit who can change firewall settings and keep a record of changes. Segment the network so a flood in one area can't take everything down. Train staff to report sudden slowness quickly.

**Detect**

- Already done: network monitoring software and the IDS/IPS.
- Still to do: set a baseline for normal traffic, alert on ICMP spikes and ICMP from untrusted outside IPs, send firewall and IDS/IPS logs to a SIEM and review them, and watch for odd activity on user accounts.

**Respond**

- Contain: block the bad traffic at the firewall, isolate affected systems, and take non-critical services offline to protect the critical ones.
- Neutralize: apply the rate limit and source IP check, make sure the IDS/IPS is catching the bad packets, and check that nothing else was compromised.
- Analyze: use firewall logs, IDS/IPS alerts, monitoring data, and packet captures to find the source, timeline, and scope.
- Improve: document what happened, tell management, and review it afterward to update the response plan.

**Recover**

- Bring back critical services first, then the rest once the flood has stopped and traffic looks normal.
- Keep ready: recent backups of firewall and network configs, a list of critical services in priority order, and a baseline of normal traffic.
- Test backups and recovery steps regularly, assign roles in the recovery plan, keep staff and clients updated during an outage, and use monitoring to confirm everything is back to normal.

## Result

The report ties this one incident to all five CSF functions. The root cause was a configuration gap, so Identify and Protect are about auditing and hardening firewalls. Detect makes sure a future flood gets noticed early, Respond covers how to contain and investigate it, and Recover covers getting services back in order. The main takeaway is that one unconfigured firewall was enough to take down the whole network, so regular configuration checks matter as much as the monitoring tools added afterward.

## Key terms

- **NIST CSF:** a voluntary framework for managing cybersecurity risk, built around Identify, Protect, Detect, Respond, and Recover.
- **DoS attack:** overwhelming a system or network with traffic so real users can't use it.
- **ICMP flood (ping flood):** a DoS attack that sends a huge number of ICMP echo requests to use up the target's network capacity.
- **Spoofed IP address:** a fake source address on a packet that hides who really sent it.
- **Rate limiting:** capping how much of a certain type of traffic is accepted.
- **Firewall:** allows or blocks traffic based on a set of rules.
- **IDS/IPS:** an IDS alerts on suspicious traffic, and an IPS can also block it.
- **SIEM:** a tool that collects logs from many sources so security events are easier to spot.
- **Least privilege:** giving people only the access they need.
- **Network segmentation:** splitting a network into zones so a problem in one doesn't spread.
