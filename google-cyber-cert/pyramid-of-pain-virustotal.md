# Pyramid of Pain: Analyzing a Malicious File with VirusTotal

Google Cybersecurity Certificate activity

## Situation

I'm a level one SOC analyst at a financial services company. An alert came in about a suspicious file on an employee's computer. The employee got an email with a password-protected spreadsheet, opened it using the password from the email, and a malicious payload ran. Multiple unauthorized executable files were created, and the intrusion detection system alerted the SOC about five minutes later. I had the SHA256 hash of the file: `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`.

## Task

Use VirusTotal to decide whether the file is malicious, then pull out three indicators of compromise (IoCs) tied to it and place them on the Pyramid of Pain.

## Action

- **Checked the verdict:** I searched the hash in VirusTotal and looked at the vendor ratio, the community score, and the security vendors' analysis on the Detection tab.
- **Found other hashes:** On the Details tab I found the other hashes for the same file (MD5, SHA-1, and more).
- **Checked network connections:** On the Relations tab I looked at contacted URLs, domains, and IP addresses and used the Detections column to separate malicious ones from normal traffic like Google and Microsoft domains.
- **Reviewed behavior:** On the Behavior tab I read the sandbox reports and the MITRE ATT&CK tactics and techniques the file used.
- **Filled in the template:** I wrote my verdict on slide 1 and put one IoC each at the Hash values, Domain names, and TTPs levels of the pyramid.

## Result

The file is malicious. 53 of 71 security vendors flagged it, the community score was -296, and vendors labeled it a trojan (Flagpro/Fragtor family). Four sandboxes also flagged it as malware. The three IoCs I recorded:

| Pyramid level | IoC |
| :-- | :-- |
| Hash values | MD5 `287d612e29b71c90aa54947313810a25` |
| Domain names | `org.misecure.com` (contacted URL `http://org.misecure.com/index.html`, flagged by 12 vendors) |
| TTPs | Execution, Credential Access, Discovery (MITRE ATT&CK) |

Hashes are the easiest IoC for an attacker to change, so blocking them helps least. TTPs are the hardest to change, so detecting behavior is more valuable. No single tool catches everything, so in a real case I would check the file with other tools too.

## Key terms

- **Indicator of compromise (IoC):** observable evidence of a possible security incident.
- **Pyramid of Pain:** model ranking IoC types by how hard it is for an attacker to change them when defenders block them (hashes, IPs, domains, network/host artifacts, tools, TTPs).
- **VirusTotal:** a crowdsourced service for checking files, domains, URLs, and IPs. Anything uploaded is shared publicly.
- **Sandbox:** isolated environment where a file is run and watched safely.
- **MITRE ATT&CK:** catalog of attacker tactics and techniques.
