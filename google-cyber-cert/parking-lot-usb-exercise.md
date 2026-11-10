# Parking Lot USB Exercise

Google Cybersecurity Certificate activity

## Situation

I played a member of the security team at Rhetorical Hospital. One morning I found a USB drive in the parking lot with the hospital's logo on it and nobody around who might have dropped it. I took it to a workstation with virtualization software, which runs a simulated computer that isn't connected to the real network, and plugged it in there so it couldn't infect anything. The drive turned out to belong to Jorge Bailey, the HR manager, and held a mix of personal and work files.

## Task

Look at what was stored on the drive without opening the files, think about how an attacker could use it against Jorge or the hospital, and write about the risks of USB baiting and the controls that could reduce them. I filled in a template with three rows: Contents, Attacker mindset, and Risk analysis.

## Action

- I reviewed the types of information on the drive. There were personal files (family and pet photos) and work files (a new hire letter and an employee shift schedule). That means PII about Jorge, his family, and his coworkers, and keeping personal and work files together on one device isn't safe.
- I thought about the drive from the attacker's side. Family details and photos could be used to write convincing phishing messages aimed at Jorge or his relatives. The shift schedule and new hire letter show who works when and who is new, which helps an attacker impersonate staff or target new hires.
- I considered that the whole thing could have been staged. The hospital logo on the drive makes it look like bait that someone left on purpose so an employee would plug it in.
- I looked at the risks of USB baiting. An infected drive could carry malware like ransomware, keyloggers, or backdoors, and if another employee plugged it into a work computer it could spread across the network and expose patient data.
- I wrote about technical controls: turn off AutoPlay, block unapproved USB ports, and scan removable media with endpoint antivirus.
- I wrote about operational controls: only inspect unknown drives in a sandbox or virtual machine, and never plug in a drive that was found.
- I wrote about managerial controls: regular security awareness training and a policy that staff must report found drives to the security team.

## Result

Even if the drive had no malicious code on it, it was still a risk, because the personal and work information on it could be used to plan phishing and social engineering attacks. A mix of technical, operational, and managerial controls covers both sides of the problem: stopping an infected drive from running, and making sure employees know what to do when they find one.

## Key terms

- **USB baiting:** an attack where a threat actor leaves a malware-loaded USB drive somewhere for a curious person to find and plug in.
- **PII (personally identifiable information):** information that can identify a person, like names, family details, or photos.
- **Social engineering:** tricking people into giving up information or access, often using personal details to seem believable.
- **Phishing:** a deceptive message meant to get someone to click a link, open a file, or share information.
- **Malware:** malicious software. Examples here are ransomware, keyloggers, and backdoors.
- **Backdoor:** a hidden way for an attacker to get into a system later.
- **Virtual machine / sandbox:** an isolated simulated computer used to safely examine unknown files or devices.
- **AutoPlay:** an operating system feature that runs a device's contents automatically when it's plugged in, which is why disabling it helps.
- **Technical, operational, and managerial controls:** security measures that use technology, day-to-day procedures, and policy or training, respectively.
