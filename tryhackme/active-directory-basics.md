# TryHackMe: Active Directory Basics

Cyber Security 101 path, Windows and AD Fundamentals module. October 2026.

Situation: Room on how Windows networks with many computers and users are managed centrally. In a real company, nobody configures each machine by hand, so a Windows domain handles it.

Task: Understand Windows domains and Active Directory, the objects inside it, how policies are applied, how authentication works, and how multiple domains connect.

Action:

- **Windows domain and domain controller:** a domain is a group of users and computers managed from one place. The domain controller (DC) is the server that runs Active Directory and authenticates everyone in the domain.
- **Active Directory objects:**
  - Users are the people (and services) that sign in.
  - Machine accounts are created for each computer, and their names end with `$`.
  - Security groups give permissions to many users at once.
  - Organizational Units (OUs) are containers used to organize objects and apply policies to them.
- **Delegation:** lets an admin give a user control over an OU, such as resetting passwords, without making them a full administrator.
- **Computer OUs:** devices are usually split into Workstations (everyday user machines) and Servers.
- **Group Policy Objects (GPOs):** collections of settings applied to OUs. They are stored in the SYSVOL share and pushed to machines.
- **Authentication:** Kerberos is the default. A user gets a Ticket Granting Ticket (TGT) from the Key Distribution Center (KDC), then uses it to request service tickets (TGS) tied to a Service Principal Name (SPN). NetNTLM is the older challenge-response method that is still supported.
- **Trees, forests, and trusts:** a tree is domains sharing a namespace, a forest is multiple trees, and trusts let users in one domain access resources in another.

Result: Completed the room. I can explain how a domain controller, OUs, GPOs, and Kerberos fit together, and why attackers focus on Active Directory.

Key terms

Windows domain, domain controller, Active Directory, machine account, security group, OU, delegation, GPO, SYSVOL, Kerberos, KDC, TGT, TGS, SPN, NetNTLM, tree, forest, trust
