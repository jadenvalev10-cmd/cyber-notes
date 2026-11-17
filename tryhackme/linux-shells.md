# Linux Shells (TryHackMe, Cyber Security 101 > Command Line)

## Situation

I wanted to get comfortable working in a Linux shell and to start automating tasks with it. The room covers how to interact with a shell, the main shell types, and writing basic bash scripts. It builds on the Linux Fundamentals module.

## Task

Learn the basic shell commands, compare the common Linux shells, write bash scripts using variables, loops and conditionals, and finish with a practical where I repair and run a script.

## Action

### Task 1: Introduction

- Learned that the shell is the layer between you and the OS. The CLI gives more power and control than the GUI, and the shell makes it easier to use.

### Task 2: Interacting with a shell

- Started the lab machine and used the shell prompt. Bash is the default shell on most distros.
- Reviewed the core commands:
  - pwd prints the working directory.
  - cd changes directory.
  - ls lists contents.
  - cat displays a file.
  - grep `<pattern>` `<file>` searches a file for a word or pattern.

### Task 3: Types of shells

- echo $SHELL shows the current shell.
- cat /etc/shells lists the installed shells.
- Typing a shell’s name (e.g. zsh) switches to it. chsh -s `<path>` changes the default permanently.
- Bash:
  - Default on most distros.
  - Has tab completion and a history file. history lists previous commands, and the arrow keys recall them.
  - Basic customization and no syntax highlighting.
- Fish:
  - The most user-friendly of the three.
  - Auto spell correction, built-in syntax highlighting, and themes.
  - Limited scripting compared to the others.
- Zsh:
  - Not the default on most distros.
  - Excellent scripting, advanced tab completion through plugins, and heavy customization through oh-my-zsh.
  - Syntax highlighting comes from plugins, and the customization can make it slower.

### Task 4: Shell scripting and components

- A script is a set of commands saved in a file so a repetitive task can be run once instead of retyped. Scripts can also be written in other languages, but this room uses bash.
- Created a .sh file with nano and started it with the shebang #!/bin/bash, which names the interpreter.
- Variables:
  - echo prints text.
  - read name stores user input in a variable, used later as $name.
- Made the script executable with chmod +x script.sh, then ran it with ./script.sh. The ./ is needed because the current directory isn’t in PATH, so the shell wouldn’t find the script otherwise.
- Loops: for i in {1..10}; do ... done repeats the code for each value. do and done mark the start and end.
- Conditionals: if ... then ... else ... fi runs code only when a condition is true. Example: ask for a name and show a secret only if it matches the authorized user.
- Comments start with # and make scripts easier to read later.

### Task 5: The locker script

- Combined variables, a loop and conditionals into one script that acts as a bank locker check.
- A for loop runs three times. An if / elif / else inside it picks which prompt to show (name, company, PIN) and stores each answer in a variable.
- After the loop, a final if compares all three answers to the allowed values. A full match grants access, and anything else prints “Authentication Denied”.

### Task 6: Practical exercise

- Became root with sudo su so the script could read every file in /var/log.
- Opened flag_hunt.sh and filled in the empty quotes: the directory to search (/var/log) and the keyword to look for. The script loops over every .log file in that directory and uses grep -q to check each one for the keyword.
- My first attempt failed because I left stray spaces inside the quotes (for example a trailing space after the keyword and in the path). A space inside the quotes becomes part of the string, so the keyword and path no longer matched anything.
- Removed the spaces, made the script executable with chmod +x, and ran it with ./flag_hunt.sh. It printed the name of the log file containing the keyword.
- My first cat attempt failed because of a space in the path (/var/log/ authentication.log).
- Used grep -n -B3 -A3 `<keyword>` `<file>` to show lines around the match and found the answer to the second question on the line above it.

## Result

I can now navigate and inspect files with core shell commands, compare bash, fish and zsh, and write and run bash scripts using variables, loops and conditionals. In the practical I debugged a script by finding the whitespace error in its quotes and used grep context flags to read the matching log entry. Next in the module is the Linux command line.

## Key terms

- Shell: the interface that takes commands and passes them to the OS.
- Bash / Fish / Zsh: three common Linux shells (Bourne Again Shell, Friendly Interactive Shell, Z Shell).
- Shebang (#!/bin/bash): the first line of a script, naming the interpreter.
- chmod +x: gives a script execute permission.
- ./script.sh: runs a script in the current directory.
- read, echo: take input into a variable and print output.
- for ... do ... done: loop.
- if ... then ... else ... fi: conditional.
- grep -B / -A: show lines before or after a match.
- /etc/shells: file listing installed shells.
- /var/log: where system logs live.
- sudo su: switch to root.
