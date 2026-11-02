# TryHackMe: Windows Fundamentals 3

Cyber Security 101 path, Windows and AD Fundamentals module. October 2026.

Situation: Final room of the Windows Fundamentals series. It covers the security features built into Windows.

Task: Learn how Windows Update, Windows Security, Defender, the firewall, SmartScreen, core isolation, BitLocker, and Volume Shadow Copy work to protect a system.

Action:

- **Windows Update:** patches are released on Patch Tuesday (the second Tuesday of the month). Updates can be postponed but not ignored forever.
- **Windows Security:** has four protection areas, and status icons are green (good), yellow (action recommended), or red (action needed).
- **Defender:** can run Quick, Full, or Custom scans and keeps a threat history. Controlled folder access protects folders from ransomware and needs real-time protection on. Exclusions can skip files, though they leave a gap.
- **Firewall:** has Domain, Private, and Public network profiles, and `wf.msc` opens the advanced settings. A public network like airport Wi-Fi should use the Public profile.
- **SmartScreen:** checks downloads and sites, with Warn, Block, or Off settings. Exploit protection adds more mitigations.
- **Core isolation:** uses virtualization to protect the core of the OS, including Memory Integrity. It relies on the TPM (Trusted Platform Module).
- **BitLocker:** encrypts a drive. Without a TPM, it can use a removable drive with a startup key.
- **Volume Shadow Copy:** keeps backup snapshots in System Volume Information. Malware often deletes them to stop ransomware recovery.
- **Living Off The Land:** attackers use tools already on the system to avoid detection.

Result: Reached 90%. I left the question about Defender update history to check on the VM directly. I can now explain what each built-in protection does and why attackers target things like shadow copies.

Key terms

Patch Tuesday, Windows Security, Defender, controlled folder access, firewall profiles (Domain, Private, Public), SmartScreen, exploit protection, core isolation, Memory Integrity, TPM, BitLocker, Volume Shadow Copy, Living Off The Land
