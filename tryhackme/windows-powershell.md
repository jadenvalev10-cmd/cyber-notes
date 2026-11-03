# TryHackMe: Windows PowerShell

Cyber Security 101 path, Command Line module. November 2026.

Situation: Easy room (about 60 minutes) and the second room in the Command Line module, after Windows Command Line. I connected to the target Windows machine over SSH from the AttackBox, landed in a normal Command Prompt, and launched PowerShell from there.

Task: Learn what PowerShell is, how its cmdlets are named, and how to use them to move around the file system, filter data, and collect system and network information.

Action:

- **What PowerShell is:** a task automation tool from Microsoft that combines a shell, a scripting language, and a configuration framework, built on .NET. It was released in 2006, and PowerShell Core (2016) made it open source and cross-platform. The big difference from older shells is that it is object-oriented: objects have properties and methods, and piping passes whole objects instead of plain text, so there is no text parsing.
- **Launching it:** from Command Prompt by typing `powershell` (what I did), or from the Start menu, Win + R, the File Explorer address bar, or Task Manager's Run new task.
- **Cmdlet basics:** cmdlets follow a Verb-Noun pattern like `Get-Content` or `Set-Location`. `Get-Command` lists what is available (filter with `-CommandType "Function"`), `Get-Help` explains a cmdlet (add `-examples` for usage), and `Get-Alias` lists shortcuts such as `dir` for `Get-ChildItem` and `cd` for `Set-Location`. `Find-Module` and `Install-Module` pull extra modules from the PowerShell Gallery, but the lab has no internet so I couldn't run them.
- **Files and folders:** `Get-ChildItem` (like `dir`), `Set-Location` (like `cd`), `New-Item` with `-ItemType File` or `Directory`, `Remove-Item` (replaces both `del` and `rmdir`), `Copy-Item`, `Move-Item`, and `Get-Content` (like `type` or `cat`).
- **Piping, filtering, sorting:** `Sort-Object` sorts by a property such as `Length`. `Where-Object -Property ... -eq ...` filters, with the operators `-ne`, `-gt`, `-ge`, `-lt`, `-le`, and `-like` for wildcard patterns. `Select-Object` picks properties, and `Select-String` searches text with regex support (like `grep` or `findstr`).
- **System and network info:** `Get-ComputerInfo` (a much fuller version of `systeminfo`), `Get-LocalUser` to list local accounts, `Get-NetIPConfiguration` and `Get-NetIPAddress` (the `ipconfig` equivalents).
- **Real-time analysis:** `Get-Process` for running processes, `Get-Service` for service status (useful for spotting suspicious or tampered services), and `Get-NetTCPConnection` for active connections, which can reveal backdoors or connections to an attacker's server. `Get-FileHash` checks file integrity, and `Get-Item -Stream *` shows NTFS Alternate Data Streams.
- **Scripting:** scripts automate repetitive work for blue team (log analysis, IOC extraction), red team (enumeration, remote execution), and admins (integrity checks, enforcing policy). `Invoke-Command` runs commands on a remote computer with `-ComputerName` and either `-ScriptBlock { ... }` or `-FilePath` for a script.
- **Hands-on challenge:** I used `Get-LocalUser` to spot an extra enabled account that was hidden among the defaults and read its description. I searched its home folder with `Get-ChildItem -Recurse -Force` (so hidden items show up), read the file I found with `Get-Content`, hashed it with `Get-FileHash` (SHA256 by default), and found a tampered service by piping `Get-Service` into `Where-Object` and matching on `DisplayName`.

Result: Completed the room. I can now navigate and manage files, filter and sort output through the pipeline, and pull system, user, process, service, and network details from PowerShell. The most useful lesson was that a service can be renamed in its display name, so I should search by more than one property when hunting for something suspicious. The next room is Linux Command Line, and I want to practice writing small scripts for repetitive checks.

Key terms

PowerShell, cmdlet, Verb-Noun, object-oriented, .NET, pipeline, alias, module, PowerShell Gallery, Get-Command, Get-Help, Get-ChildItem, Where-Object, Select-Object, Select-String, Get-LocalUser, Get-Process, Get-Service, Get-NetTCPConnection, Get-FileHash, Alternate Data Stream (ADS), Invoke-Command, ScriptBlock
