# TryHackMe: Linux Fundamentals Part 1

Cyber Security 101 path, Linux Fundamentals module. October 2026.

Situation: Easy room (about 15 minutes) and my first hands-on time in a Linux terminal, using an Ubuntu machine in the browser. Linux runs websites, car panels, point-of-sale systems, traffic lights, industrial sensors, and phones.

Task: Learn the core commands for finding out who I am on the system, moving around the file system, searching for files and text, and combining commands.

Action:

- Deployed the lab machine, and shut it down when I was done.
- Used `whoami` to see which user I was, and `echo` to print text (quotes are needed for more than one word).
- Used `ls` to list files, `cd` to change folders, `cat` to read a file, and `pwd` to show the working directory. I first ran `cat` on a folder and it failed. The fix was to `ls` first, `cd` into the folder, and then `cat` the file.
- Used `find -name <file>` to locate a file, and `grep "<text>" <file>` to search inside a long web server `access.log`.
- Learned the operators: `&` runs a command in the background, `&&` runs the second command only after the first finishes, `>` redirects output to a file (overwriting it), and `>>` appends to a file. I tried `echo > file` and then `>>` and checked the results with `cat`.

Result: Completed the room. I can check my user, navigate and read files, search logs with `grep`, and redirect output without overwriting a file by accident.

Key terms

Terminal / command line, whoami, echo, ls, cd, cat, pwd, working directory, find, grep, log file, operator, `&`, `&&`, `>`, `>>`, redirection
