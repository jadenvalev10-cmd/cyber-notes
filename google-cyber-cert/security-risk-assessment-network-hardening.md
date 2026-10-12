# Security Risk Assessment: Network Hardening

Google Cybersecurity Certificate activity

## Situation

A social media organization had just suffered a major data breach that exposed customers' personal information, such as names and addresses. Acting as a security analyst, I inspected the network and found four vulnerabilities:

1. Employees share passwords.
2. The database admin password is still set to the default.
3. The firewalls have no rules filtering traffic in or out of the network.
4. Multifactor authentication (MFA) is not used.

Without action, the organization is at risk of another breach or attack.

## Task

Choose up to three network hardening tools or methods that can be applied consistently to prevent future breaches, and explain why each one is effective and how often it needs to be implemented. I completed both parts of the security risk assessment template, using the Network hardening tools reference sheet as supporting material.

## Action

- Matched each vulnerability to a hardening task from the reference sheet: shared and default passwords map to password policies, missing MFA maps to MFA, and the unfiltered network maps to firewall maintenance.
- Part 1, selected tools and methods:
  - Implement multifactor authentication (MFA) for all employees and administrators.
  - Enforce a strong password policy, and replace the default database admin password. Passwords must not be shared between employees.
  - Perform regular firewall maintenance, including configuring and updating rules that filter incoming and outgoing network traffic.
- Part 2, explained why each is effective:
  - MFA: users verify their identity in two or more ways (for example a password plus a one-time password, badge, or fingerprint). A shared, guessed, or stolen password is not enough to log in, and the second factor is tied to one person, which discourages sharing. It also helps against brute force attacks. It is mostly set up once and then maintained, and reviewed periodically.
  - Password policy: following NIST's latest guidance, focus on salting and hashing stored passwords rather than requiring overly complex passwords or frequent changes. Passwords are unique and never shared, and accounts lock after repeated failed attempts. The default admin password is changed immediately because default credentials are publicly known. The default change is one-time; the policy is enforced continuously and reviewed regularly.
  - Firewall maintenance: check and update firewall configurations regularly. Add rules that allow only necessary traffic, restrict database access to approved internal systems, and block unknown external sources. This protects against threats such as DDoS attacks and limits damage if a system is compromised. Review on a schedule (for example monthly or quarterly) and after any event that lets abnormal traffic in.

## Result

Together the three measures cover all four vulnerabilities. MFA and the password policy secure the credential layer, and firewall rules secure the network layer. Combining preventive controls at both layers means one failure, such as a stolen password, is less likely to lead to another breach.

## Key terms

- **Network hardening:** strengthening a network's security by reducing its attack surface and tightening configurations, repeated consistently over time.
- **Multifactor authentication (MFA):** requiring two or more forms of verification to access a system.
- **Brute force attack:** repeatedly guessing passwords, manually or with a script, until one works.
- **Salting and hashing:** adding random data to a password and running it through a one-way function so stored passwords are hard to recover.
- **Default credentials:** factory-set usernames and passwords that are publicly documented and must be changed.
- **Firewall rules:** settings that allow or block network traffic by source, destination, port, or protocol.
- **DDoS (distributed denial of service):** an attack that floods a system with traffic from many sources so it cannot serve real users.
