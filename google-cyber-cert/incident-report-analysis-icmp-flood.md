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
# Incident Report Analysis: ICMP Flood (DoS) and the NIST CSF

Google Cybersecurity Certificate activity

## Situation

I took the role of a cybersecurity analyst at a multimedia company that offers web design, graphic design, and social media marketing to small businesses. The company's internal network stopped responding for two hours when a flood of ICMP packets overwhelmed it, so normal internal traffic could not reach network resources.

The incident management team blocked incoming ICMP packets, took non-critical network services offline, and restored critical services. The cybersecurity team's investigation found that a malicious actor sent a flood of ICMP pings into the network through an unconfigured firewall, which allowed a denial of service (DoS) attack.

To address the event, the network security team added:

1. A firewall rule that limits the rate of incoming ICMP packets.
2. Source IP address verification on the firewall to check for spoofed addresses on incoming ICMP packets.
3. Network monitoring software to detect abnormal traffic patterns.
4. An IDS/IPS system to filter out some ICMP traffic based on suspicious characteristics.

## Task

Use the NIST Cybersecurity Framework (CSF) to analyze the event and turn it into a plan to improve the company's network security. I completed the incident report analysis template by writing a summary of the event and then one section for each CSF function: Identify, Protect, Detect, Respond, and Recover.

## Action

- **Summary:** The network was down for two hours because of an ICMP flood sent through an unconfigured firewall. Critical services were restored by blocking ICMP, taking non-critical services offline, and then adding new controls.
- **Identify:**
  - Attack type: denial of service (DoS), specifically an ICMP flood (ping flood), possibly using spoofed source IP addresses.
  - Systems affected: the internal network and every service that depends on it, plus the perimeter firewall, which was the entry point because it was unconfigured.
  - Root cause: no firewall rule to filter or limit incoming ICMP packets, and no source IP verification.
  - Impact: about two hours of outage that disrupted normal business operations.
  - Next step: audit all firewalls, network devices, and access privileges for similar gaps.
- **Protect:**
  - Already in place: the ICMP rate-limiting rule and source IP address verification.
  - Planned: review and harden every firewall and router against a documented baseline on a regular schedule, keep rules and firmware up to date, and allow only the ICMP types the business needs.
  - Planned: limit who can change firewall configuration (least privilege) with a documented change process, segment the network so a flood in one area cannot take down critical services, and train staff to report sudden slowdowns quickly.
- **Detect:**
  - Already in place: network monitoring software and an IDS/IPS that filters suspicious ICMP traffic.
  - Planned: establish a baseline of normal traffic, alert on ICMP volume spikes and ICMP from untrusted external IPs, collect firewall and IDS/IPS logs in a SIEM tool and review them regularly, and watch for unusual activity on user accounts.
- **Respond:**
  - Contain: block the offending traffic at the firewall, isolate affected segments and devices, and take non-critical services offline to protect critical ones.
  - Neutralize: apply the rate limit and source IP verification, confirm the IDS/IPS is filtering malicious packets, and check that no other system was compromised.
  - Analyze: use firewall logs, IDS/IPS alerts, monitoring data, and packet captures to find the source, timeline, and scope.
  - Improve: document the incident, notify management, and hold a lessons-learned review to update the incident response plan.
- **Recover:**
  - Restore critical services first, then non-critical services once the flood has stopped and normal traffic is confirmed.
  - Keep current backups of firewall and network configurations, a prioritized inventory of critical services, and known-good traffic baselines ready.
  - Test backups and recovery procedures regularly, keep a recovery plan with assigned roles, communicate status to staff and clients, and confirm through monitoring that traffic has returned to normal.

## Result

The completed report links one incident to all five CSF functions. The root cause was a configuration gap, so Identify and Protect focus on auditing and hardening firewalls. Detect adds visibility so a future flood is caught early, Respond defines how to contain and analyze an incident, and Recover defines how to restore services in priority order. The main lesson is that a single unconfigured firewall can allow a basic ICMP flood to take down an entire internal network, so routine configuration audits matter as much as the detection tools added afterward.

## Key terms

- **NIST Cybersecurity Framework (CSF):** a voluntary set of standards, guidelines, and best practices for managing cybersecurity risk, organized into functions such as Identify, Protect, Detect, Respond, and Recover.
- **Denial of service (DoS) attack:** an attack that overwhelms a system or network with traffic so legitimate users cannot access it.
- **ICMP flood (ping flood):** a DoS attack that sends a large volume of ICMP echo request packets to exhaust a target's network capacity.
- **Spoofed IP address:** a forged source address on a packet that hides the real sender.
- **Rate limiting:** capping how much traffic of a given type is accepted over time.
- **Firewall:** a device or software that allows or blocks network traffic based on a set of rules.
- **IDS/IPS:** an intrusion detection system alerts on suspicious traffic, and an intrusion prevention system can also block it.
- **SIEM:** a tool that collects and analyzes logs from many sources to surface security events.
- **Least privilege:** giving users and administrators only the access they need to do their jobs.
- **Network segmentation:** splitting a network into separate zones so a problem in one area does not spread to others.
