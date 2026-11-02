# Risk Register: Commercial Bank

Google Cybersecurity Certificate activity

## Situation

I joined a cybersecurity team at a commercial bank that was running a risk assessment. The bank is in a coastal area with low crime, has 100 on-premise and 20 remote employees, 2,000 individual accounts and 200 commercial accounts, and strict financial regulations. The team kept a risk register, a central record of risks to the bank's assets, and wanted help prioritizing the risks to the bank's funds.

## Task

Score each of five risks for likelihood (1 to 3) and severity (1 to 3), then multiply them (Likelihood x Impact = Risk) to get a priority from 1 to 9. I also wrote a short note on how security events are possible in this environment.

## Action

I wrote the note first: the coastal location exposes the bank to natural disasters that can disrupt supply chains, and 120 employees plus over 2,200 accounts create many points where human error, phishing, or weak data protection could expose funds. The strict regulations raise the stakes.

For each risk, I scored likelihood by how often it could realistically happen. I scored severity by financial harm, impact on operations, regulatory violations, and reputation.

- **Financial records leak:** a backup database server is publicly accessible, so the exposure already exists. A leak could mean fines, lost customers, and reputational damage.
- **Business email compromise:** with 120 staff, phishing is a constant threat. The damage is usually limited, so severity is moderate.
- **Compromised user database:** poorly encrypted customer data makes a breach plausible but not constant. Severity is high because it affects customer data and regulations.
- **Theft:** the area has low crime, so it is unlikely. An unlocked safe would still be costly.
- **Supply chain disruption:** hurricanes are infrequent, and the bank can usually recover from a delay.

## Result

| Risk | Likelihood | Severity | Priority |
|---|---|---|---|
| Financial records leak | 3 | 3 | 9 |
| Business email compromise | 3 | 2 | 6 |
| Compromised user database | 2 | 3 | 6 |
| Theft | 1 | 3 | 3 |
| Supply chain disruption | 1 | 2 | 2 |

The financial records leak ranked highest, so the exposed backup server should be fixed first. Scoring the risks this way gives the team a clear order to spend time and money in.

## Key terms

- **Risk register:** a central record of risks to an organization's assets, systems, and data.
- **Asset:** what is at risk of being harmed, damaged, or stolen.
- **Likelihood:** how likely a risk is to cause a security event.
- **Severity:** how much damage the event could do.
- **Risk = Likelihood x Impact:** the formula used to set priority.
- **NIST CSF:** a framework that starts with assessing risk.
