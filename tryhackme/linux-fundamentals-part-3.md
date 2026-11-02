# TryHackMe: Linux Fundamentals Part 3

Cyber Security 101 path, Linux Fundamentals module (final room). October 2026.

Situation: The last room in the Linux module, covering the tools used to actually work on a Linux system. I connected over SSH from the AttackBox. A lot of it was confusing at first, so these notes are for me to come back to.

Task: Learn text editors, ways to download and transfer files, how processes work, how to schedule tasks, how packages are installed, and how logging works.

Action:

- **Text editors:** `nano <file>` opens a simple editor. Ctrl+O saves, Ctrl+X exits, Ctrl+W searches, Ctrl+K cuts a line, Ctrl+U pastes, and Ctrl+_ jumps to a line number. Vim is more advanced and customizable, with syntax highlighting.
- **Utilities:** `wget` downloads a file over HTTP. `scp` copies files over SSH, written as source first and then destination, with the remote side as `user@ip:path`. `python3 -m http.server` serves the current folder on port 8000, so a second terminal is needed to `wget` from it. Ctrl+C stops the server. I moved a hidden file between the lab machine and the AttackBox this way.
- **Processes:** a process is a running program and gets a PID. `ps`, `ps aux`, and `top` show what is running, and `kill <PID>` stops one. SIGTERM asks a process to stop cleanly, SIGKILL stops it with no cleanup, and SIGSTOP pauses it. Namespaces isolate the resources a process can see. `systemd` is the first process (PID 1) and the parent of everything else. `systemctl start/stop` act now, while `enable/disable` control what happens at boot. I also used `&` to background a command, Ctrl+Z to suspend it, and `fg` to bring it back.
- **Cron:** `crontab -e` edits scheduled jobs and `crontab -l` lists them. A cron line has five time fields (minute, hour, day of month, month, day of week) and then the command. `*` means any value and `*/12` means every 12.
- **Packages:** `apt` installs software from repositories, and GPG keys verify that the source is trusted. The order is: add the key, add the repository file, run `apt update`, then `apt install`. `apt remove` takes software off. `dpkg` can install a package too, but `apt` handles dependencies and updates.
- **Logs:** logs live in `/var/log` and are rotated automatically. The Apache access log records each request (IP, timestamp, request, status, size) and the error log records problems. Tools like fail2ban and UFW protect against brute force and filter traffic. I read an access log to find a visitor's IP and the file they requested.

Result: Completed the room. The parts I want to review again are the `scp` direction, the Python web server with a second terminal, how cron fields work, the difference between `systemctl start` and `enable`, the apt order of operations, and `&` versus Ctrl+Z versus `fg`.

Key terms

nano, Vim, wget, scp, `python3 -m http.server`, process, PID, ps, top, kill, SIGTERM, SIGKILL, SIGSTOP, systemd, systemctl, cron, crontab, apt, GPG key, repository, dpkg, `/var/log`, access log, fail2ban, UFW
