# TryHackMe: Windows Command Line

Cyber Security 101 path, Command Line module. October 2026.

Situation: Easy room (about 45 minutes) that shows why the command line is useful and how to use it on Windows. I connected to the target machine over SSH from the AttackBox. This is a different room from the earlier Windows CLI Basics.

Task: Learn the main commands for system information, networking, files and folders, processes, and system maintenance.

Action:

- **Why use the CLI:** it uses fewer resources, makes automation possible, and allows remote management over SSH. The default interpreter is `cmd.exe`.
- **System info:** `set` shows environment variables (including Path), `ver` shows the Windows version, and `systeminfo` shows detailed system details. Piping into `more` pages long output. `help`, `cls`, and Ctrl+C are also useful.
- **Networking:** `ipconfig` and `ipconfig /all` (MAC address, DHCP, DNS), `ping` (tests reachability using ICMP), `tracert` (follows the route using TTL), `nslookup` (DNS lookups, with an optional DNS server), and `netstat -abon` (`-a` all connections, `-b` the program, `-o` the PID, `-n` numeric).
- **Files and folders:** `cd`, `dir` (`/a` shows hidden files, `/s` includes subfolders), `tree`, `mkdir`, `rmdir`, `type`, `more`, `copy`, `move`, `del` / `erase`, and the `*` wildcard.
- **Processes:** `tasklist`, filtered with `tasklist /FI "imagename eq ..."`, and `taskkill /PID` to end one.
- **Maintenance:** `chkdsk` checks a disk, `driverquery` lists drivers, `sfc /scannow` repairs system files, and `shutdown` with `/s`, `/r`, or `/a` shuts down, restarts, or aborts.

Result: Completed the room. I can gather system and network information, work with files, and manage processes from the command line. The next step is Windows PowerShell, and practicing scripts for repetitive checks.

Key terms

cmd.exe, environment variable, systeminfo, pipe, ipconfig, ping, ICMP, tracert, TTL, nslookup, netstat, tasklist, taskkill, PID, chkdsk, sfc, shutdown, wildcard
