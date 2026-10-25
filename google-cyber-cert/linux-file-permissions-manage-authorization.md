l# Linux File Permissions: Manage Authorization

Google Cybersecurity Certificate activity

## Situation

I'm a security professional at a large organization, working mostly with the research team. Part of my job is making sure users only have the permissions they need. The files in the projects directory belonged to researcher2, and I had to check whether their permissions matched the access they should actually allow.

## Task

Review the permissions in the projects directory (including hidden files), find anything that doesn't match the organization's rules, and fix it with Linux commands:

- No file may be writable by "other".
- The archived hidden file `.project_x.txt` should be read-only for the user and group, with no write access for anyone.
- Only researcher2 should have access to the `drafts` directory.

## Action

**Checked permissions.** I ran `ls -la` in the projects directory. `-l` is the long format (permissions, owner, group, size, date) and `-a` includes hidden files, which start with a period.

```
drwx--x---  researcher2 research_team  drafts
-rw--w----  researcher2 research_team  .project_x.txt
-rw-rw-rw-  researcher2 research_team  project_k.txt
-rw-r-----  researcher2 research_team  project_m.txt
-rw-rw-r--  researcher2 research_team  project_r.txt
-rw-rw-r--  researcher2 research_team  project_t.txt
```

**Read the permission string.** Using `drwx--x---` (drafts) as the example: character 1 is the type (`d` = directory, `-` = file), characters 2-4 are the user's permissions (`rwx`), 5-7 are the group's (`--x`), and 8-10 are other's (`---`). `r` is read, `w` is write, `x` is execute, and `-` means not granted.

**Removed write from other.** `project_k.txt` was `-rw-rw-rw-`, the only file where other could write.

```
chmod o-w project_k.txt
```

**Locked down the hidden archive file.** `.project_x.txt` was `-rw--w----`. I removed write from the user and group and added read for the group. Multiple changes are separated by commas with no spaces.

```
chmod u-w,g-w,g+r .project_x.txt
```

**Restricted the drafts directory.** It was `drwx--x---`, so the group could still enter it. I removed execute from the group.

```
chmod g-x drafts
```

After each change I ran `ls -la` again to confirm.

## Result

| Item | Before | After |
| :-- | :-- | :-- |
| `project_k.txt` | `-rw-rw-rw-` | `-rw-rw-r--` |
| `.project_x.txt` | `-rw--w----` | `-r--r-----` |
| `drafts` | `drwx--x---` | `drwx------` |

Other can no longer write to any file, the archived file is read-only for the user and group, and only researcher2 can access `drafts`. This is least privilege: each user gets only the access they need.

## Key terms

- **Authorization**: what a user is allowed to do on a system.
- **Least privilege**: giving users only the minimum access they need.
- **chmod**: the command that changes file and directory permissions (`u`, `g`, `o` for user, group, other; `+` and `-` to add or remove).
- **Hidden file**: a file whose name starts with a period, shown with `ls -a`.
