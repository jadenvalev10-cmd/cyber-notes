# Add and Manage Users with Linux Commands

Google Cybersecurity Certificate activity

## Situation

I was working as a security analyst in a Linux lab where I needed to manage user accounts. Controlling who has an account, and what that account can reach, is a basic part of authorization. Accounts that are no longer needed are a risk if they stay around.

## Task

Go through the life of a user account: add a user, change their group, give them ownership of a file, add them to a second group, and then remove the account and clean up.

## Action

**Added a user.** I created the account with `sudo useradd researcher9`. Creating accounts needs elevated privileges, which is why `sudo` is there.

**Changed the primary group.** `sudo usermod -g research_team researcher9` made `research_team` the user's primary group.

**Changed file ownership.** `sudo chown researcher9 project_r.txt` made the new user the owner of the file. I checked it with `ls -l` to confirm the owner changed.

**Added a supplementary group.** `sudo usermod -a -G sales_team researcher9` added a second group. The lowercase `-a` means append, so the user keeps their existing groups, and the uppercase `-G` is the supplementary group option. Leaving out `-a` would replace the user's groups instead of adding one.

**Removed the user.** `sudo userdel researcher9` deleted the account.

**Cleaned up the leftover group.** Adding the user also created a group with the same name, and deleting the user did not remove it. I ran `sudo groupdel researcher9` to finish the cleanup.

## Result

I added, modified, and removed a user account from the command line and checked each change along the way. The main takeaway is that removing a user is not just deleting the account. Leftover groups and files they own still need attention so stale access does not stick around.

## Key terms

- **Authentication vs. authorization:** authentication proves who you are, authorization decides what you can do.
- **useradd, usermod, userdel:** add, change, and remove user accounts.
- **Primary vs. supplementary group:** `-g` sets the primary group, `-a -G` adds an extra one.
- **chown:** changes the owner of a file.
- **groupdel:** removes a group.
- **Least privilege:** give users only the access they need, and remove it when they no longer need it.
