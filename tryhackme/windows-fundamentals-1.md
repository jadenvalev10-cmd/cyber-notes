# TryHackMe: Windows Fundamentals 1

Windows Fundamentals module. October 2026.

Situation: First room of the Windows Fundamentals series. It covers how a Windows desktop is laid out and how the system is organized, using a Windows machine in the browser.

Task: Learn the basics of Windows editions, the desktop, the file system, user and group management, UAC, the settings tools, and Task Manager.

Action:

- Looked at the Windows editions and the desktop interface.
- **File system:** Windows uses NTFS. Compared to the older FAT formats, NTFS is journaling, which helps it recover after a failure, and supports file permissions, encryption, and large files.
- **System folders:** `C:\Windows` is the core of the OS. `System32` inside it holds the files Windows depends on to run, and `%windir%` is the environment variable that points to the Windows folder.
- **Users and groups:** managed with `lusrmgr.msc`. Groups give permissions to every account in them, so it's easier than setting access per user.
- **UAC (User Account Control):** asks for approval when a change needs administrator rights. It does not prompt for the built-in Administrator account.
- **Settings vs. Control Panel:** Settings is the newer interface and Control Panel is the older one with more detailed options.
- **Task Manager:** shows running processes and resource use, and can end a process. It opens with Ctrl+Shift+Esc.

Result: Completed the room. I can find my way around Windows, explain NTFS versus FAT, locate the key system folders, manage users and groups, and use UAC and Task Manager.

Key terms

NTFS, FAT, journaling, `C:\Windows`, System32, `%windir%`, lusrmgr.msc, user, group, UAC, Settings, Control Panel, Task Manager
