# TryHackMe: Windows Fundamentals 2

Cyber Security 101 path, Windows and AD Fundamentals module. October 2026.

Situation: Second room of the Windows Fundamentals series. It goes into the built-in tools that administrators and analysts use to see what a Windows machine is doing.

Task: Learn the system configuration tools, UAC settings, Computer Management, System Information, Resource Monitor, the command line basics, and the Registry Editor.

Action:

- **MSConfig:** has five tabs (General, Boot, Services, Startup, Tools). On Windows Server, startup items are found with `shell:startup`. The page file is virtual memory, and the Startup and Recovery settings control what kind of crash dump is saved (automatic, kernel, small, complete, or none).
- **UAC:** has four levels (always notify, notify only for apps, notify without dimming the screen, and never notify). The default is to notify for apps. The settings open with `UserAccountControlSettings.exe`.
- **Computer Management (`compmgmt.msc`):**
  - Task Scheduler runs tasks at set times or events. Checking it can reveal tasks that run at startup.
  - Event Viewer holds the system logs.
  - Shared Folders shows shares, sessions, and open files. Shares ending in `$` are hidden, like `C$` and `ADMIN$`.
  - It also has local users and groups, Performance Monitor, Device Manager, Disk Management, and Services, where startup types are Automatic, Manual, or Disabled.
  - It also includes WMI. WMIC is deprecated and PowerShell replaces it.
- **System Information (`msinfo32.exe`):** summarizes hardware resources, components, and the software environment, including environment variables.
- **Resource Monitor (`resmon.exe`):** shows CPU, memory, disk, and network use per process.
- **Command line:** `hostname`, `whoami`, `ipconfig /all`, `netstat`, and `net help <subcommand>` for details.
- **Registry Editor:** a database of low-level settings for Windows and its programs. I looked at how it's launched and what it holds.
- Most of these tools can be launched from the Start menu or Run without going through MSConfig.

Result: Reached 94%. I skipped one question about a hidden share on the VM, which I can find in Computer Management under Shared Folders and then Shares. I can now open the main admin tools and explain what each one shows.

Key terms

MSConfig, page file, crash dump, UAC levels, Computer Management, Task Scheduler, Event Viewer, hidden share (`$`), Services, WMI, msinfo32, environment variable, Resource Monitor, Registry Editor
