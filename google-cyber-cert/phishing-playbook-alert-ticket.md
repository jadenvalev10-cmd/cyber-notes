# Phishing Playbook: Escalating a Malicious Attachment Alert

Google Cybersecurity Certificate activity

## Situation

I'm a level one SOC analyst at a financial services company. A phishing alert (ticket A-2703, severity Medium) came in saying an employee may have opened a malicious email and its attachment. The email was sent on July 20, 2022 at 09:30:14 AM to the HR mailbox from "Def Communications" <76tguyhh6tgftrt7tg.su> (114.114.114.114), with an attachment named bfsvc.exe. I had already verified the attachment's SHA256 hash as malicious in the Pyramid of Pain activity: 54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b.

## Task

Follow the phishing playbook and flowchart to evaluate the alert, decide whether to escalate or close it, and update the alert ticket with my status and comments.

## Action

- Started the ticket: I changed the ticket status to Investigating. I began at playbook step 2 (Evaluate the alert) because the alert had already been received.
- Evaluated the alert ticket: I checked the severity (Medium, which the playbook says is a sign a ticket might need escalation), the sender details, the subject line and message body, and the attachment.
- Answered the 5 W's: Who: a sender using the name "Def Communications" and signing as "Clyde West". What: a phishing email with a malicious .exe attachment that was opened. When: July 20, 2022 at 09:30:14 AM. Where: the HR mailbox and the employee's computer at the company. Why: the attacker wanted the employee to run malware.
- Checked for links and attachments (playbook steps 3.0 and 3.1): the email has an attachment, and its hash was already verified as malicious, so the alert needed to be escalated (step 3.2).
- Updated the ticket: I set the status to Escalated and wrote a comment with a short summary of the alert and three reasons for escalating.

## Result

I escalated the ticket to a level-two analyst. My three reasons:

- The attachment's hash is a verified malicious file, and it is an executable (.exe) even though the email says it is a resume and cover letter.
- The sender details don't match. The display name is "Def Communications" but the address is a random string on a .su domain, the email is signed "Clyde West", and the subject is a "Re:" reply to a thread HR never started.
- The email has typos ("Egnieer" in the subject, "I am writing for to express" in the body) and puts the attachment's password in the message, which is a common way to get past email scanning.

Because the file was opened on an employee's computer, the next steps for the level-two analyst are to isolate the affected machine and investigate further. A playbook keeps the response consistent and fast, but it isn't a full guide, since every organization has its own procedures.

## Key terms

- Phishing: using email or messages to trick someone into opening a malicious attachment or link or giving up information.
- Playbook: a set of step-by-step instructions for responding to a specific type of security incident.
- Alert ticket: the record of an alert that tracks its status (Open, Investigating, Escalated, Closed) and the analyst's comments.
- Escalation: passing an incident to a more senior analyst or team when it needs more investigation or action.
- 5 W's: who, what, when, where, and why, used to understand an incident.
