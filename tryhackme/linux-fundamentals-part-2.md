# TryHackMe: Linux Fundamentals Part 2

Cyber Security 101 path, Linux Fundamentals module. October 2026.

Situation: Easy room (about 25 minutes) that follows Part 1. This time I logged in to a separate lab machine over SSH from the AttackBox.

Task: Learn how to log in remotely, use command arguments, manage files, know the important Linux directories, and switch between users.

Action:

- Set up the idea of two machines: the AttackBox is my own computer, and the lab machine is the one I log in to.
- Used SSH, a secure way to log in to another machine remotely. It needs an IP address and a username and password, written as `ssh user@ip`. The password doesn't show as you type it.
- Learned that `ls -a` shows hidden files (ones that start with a dot), and `ls -lh` shows details in a readable format. `--help` and `man <command>` explain how a command works.
- Managed files with `touch` (create a file), `mkdir` (create a folder), `cp` (copy), `mv` (move or rename), and `rm` (delete, with `-R` for folders). Full paths work with all of them.
- Learned the key directories: `/` is the root of the file system, `/etc` holds config files (including sudoers), `/var` holds data like logs in `/var/log`, `/root` is the root user's home folder (not `/home/root`), and `/tmp` is temporary storage that any user can write to and that clears on restart.
- Used `ls -l` to read permissions (read, write, execute) for the owner and the group, and `su -l <user>` to switch to another user with a login shell to reach a file I could not read before.

Result: Completed the room. I can SSH into a machine, show hidden files, read man pages, create and move files, recognize the key directories, and switch users to get at restricted files.

Key terms

SSH, AttackBox, argument / flag, `--help`, man page, hidden file, touch, mkdir, cp, mv, `rm -R`, root (`/`), `/etc`, `/var`, `/root`, `/tmp`, owner, group, read / write / execute, `su -l`
