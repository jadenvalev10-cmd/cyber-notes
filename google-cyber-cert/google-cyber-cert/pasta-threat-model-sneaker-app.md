# PASTA Threat Model: Sneaker App

Google Cybersecurity Certificate activity

## Situation

I'm on the security team at a company for sneaker enthusiasts and collectors. The business is about to launch a mobile app that lets customers buy and sell shoes. Before launch, I needed to work out whether the app was safe to release, so I threat modeled it with PASTA (Process of Attack Simulation and Threat Analysis), a seven-stage framework for assessing the risk profile of a new application.

## Task

Go through all seven PASTA stages and fill in the worksheet: business objectives, technical scope, threats, vulnerabilities, and security controls.

## Action

- **Stage I, define objectives:** I pulled three business objectives from the app description. Connect buyers and sellers with easy sign-up, login, account management, messaging, and seller ratings. Protect user data privacy so customers trust the company. Process sales quickly and clearly with several payment options, handled properly to avoid legal issues.
- **Stage II, define the technical scope:** The app uses APIs, PKI (AES and RSA), SHA-256, and SQL. I picked the API to evaluate first, because it connects sellers, buyers, and payment providers, it is exposed to the internet, and third-party APIs sit outside the company's control.
- **Stage III, decompose the application:** I reviewed the data flow diagram for a buyer searching the database and looked at where the API, encryption, hashing, and SQL protect user data along the way.
- **Stage IV, threat analysis:** Internal threat: an employee with more access than they need, or one who gets tricked by social engineering. External threat: phishing, malware, or stolen credentials used to take over buyer and seller accounts.
- **Stage V, vulnerability analysis:** SQL injection, where a search or login field that doesn't validate input lets an attacker run their own queries against the database. Broken authentication, where weak password rules and no multi-factor authentication let attackers brute-force or reuse stolen credentials.
- **Stage VI, attack modeling:** I reviewed the attack tree to see how a threat actor could chain attack vectors together to reach user data.
- **Stage VII, risk analysis and impact:** I chose four controls: input validation with prepared statements, multi-factor authentication with strong passwords, the principle of least privilege, and encryption plus salted hashing.

## Result

I finished the PASTA worksheet for all seven stages. The biggest risks are user input reaching the database and account takeover, so those controls should be in place before the app launches.

## Key terms

- **PASTA:** Process of Attack Simulation and Threat Analysis, a seven-stage threat modeling framework.
- **API:** a set of rules that define how software components interact with each other.
- **PKI:** public key infrastructure, an encryption framework that secures the exchange of online information (here AES for sensitive data and RSA for key exchange).
- **SHA-256:** a hash function that turns any input into a 256-bit digest.
- **SQL injection:** an attack that sneaks malicious SQL into an input field so the database runs it.
- **Prepared statements:** queries that keep user input separate from the SQL code, which blocks SQL injection.
- **Broken authentication:** weak login protections, such as weak passwords or no MFA, that let attackers take over accounts.
- **MFA:** multi-factor authentication, requiring more than one way to prove identity.
- **Principle of least privilege:** users get only the minimum access needed to do their job.
- **Salting:** adding random data to a password before hashing so identical passwords don't produce identical hashes.
- **Data flow diagram:** a map of how information moves through an application.
- **Attack tree:** a diagram of the paths an attacker could take to reach a goal.
