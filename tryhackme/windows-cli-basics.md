# TryHackMe: Windows CLI Basics

Pre Security path, Operating Systems Basics module (Easy, 60 min). Completed.

**Situation:** Continuing the Operating Systems Basics module, moved into the Windows counterpart to Linux CLI Basics to get comfortable navigating and querying a Windows system via Command Prompt.

**Task:** Learn to navigate the Windows filesystem, find a file when given only its name (not its location), read its contents, and gather basic system and network information, all via the CLI instead of the GUI.

**Action:**

- **Orientation and file hunt:** `cd` (with no arguments) to show the current directory, `dir` to list contents, `dir /a` to reveal hidden files and folders, and `cd <folder>` to move between directories.
- Used `dir /s task_brief.txt` to search all subfolders and return the file's full path, ran `cd` to it, confirmed with `dir`, and read it with `type task_brief.txt` (it revealed a message and flag left as a note).
- **System and network recon:** `whoami` (current logged-in user), `hostname` (computer name), `systeminfo` (OS name, OS version, system type), and `ipconfig` (IPv4 address, default gateway).

**Result:** Completed the room. Located and read `task_brief.txt` by searching rather than guessing, and could report the logged-in user, computer name, Windows version, and network config. The Conclusion task reinforced why these are foundational IT and security skills: speed, precision, automation, and visibility beyond the GUI.

## Key commands

| Command | Purpose |
| :-- | :-- |
| `cd` | Show or change the current directory |
| `dir` | List contents |
| `dir /a` | Show hidden files and folders |
| `dir /s <filename>` | Search subfolders for a file |
| `type <filename>` | Print file contents |
| `whoami` | Current user |
| `hostname` | Computer name |
| `systeminfo` | OS and version details, system type |
| `ipconfig` | Network config (IPv4, default gateway) |
