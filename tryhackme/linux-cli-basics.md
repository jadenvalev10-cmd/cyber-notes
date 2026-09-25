# TryHackMe: Linux CLI Basics

Pre Security path, Operating Systems Basics module. Completed.

**Situation:** In the room's scenario, it is the first day on a Cyber Operations Support Team. A guided lab machine is used to get comfortable navigating the Linux command line before moving on to file permissions, users and groups, and real security tooling.

**Task:** Learn core navigation and inspection commands, then use them independently to complete two "find and read" missions and a system health check: locating hidden notes left by a supervisor and reporting back basic system info.

**Action:**

- **Orientation:** `pwd`, `ls` / `ls -l` / `ls -al`, `cd` / `cd ..`
- **File hunting:** `find ~ -name <filename>`
- **Reading files:** `cat`
- **Mission 1:** used find + cat to locate and read `mission_brief.txt`, which held a hidden flag and the next assignment.
- **System report:** `whoami`, `uname -a`, `df -h`, and `cat` on `os-release` in `/etc`.
- **Unassisted mini-challenge:** used find + cat again to locate `day1_report.txt` in a hidden nested folder (`~/.logs/archive/`) and read its closing message and flag.

**Result:** Completed the room. Collected both hidden flags, correctly reported the username, kernel version, free disk space, and distro, and can now navigate and search an unfamiliar Linux filesystem without step-by-step guidance.
