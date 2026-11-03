# Create Hash Values

Google Cybersecurity Certificate activity

## Situation

I was working as a security analyst in a Linux lab where I needed to figure out whether two files were really the same. I was logged in as the user analyst in /home/analyst, which held two files, file1.txt and file2.txt. When I looked at them they seemed to contain the same data, but I couldn't trust my eyes alone, since a single changed character can turn a legitimate file into a malicious copy.

## Task

Use Linux commands to display both files, generate a hash for each one, and compare the hashes by hand to find out if the files were identical or different.

## Action

- I ran `ls` to list the directory and confirmed file1.txt and file2.txt were there.
- I used `cat file1.txt` and `cat file2.txt` to display each file. The contents looked identical on screen.
- I generated a hash for each file with `sha256sum file1.txt` and `sha256sum file2.txt`. This prints the SHA-256 hash value (a 64-character hexadecimal string) followed by the file name.
- I ran `sha256sum file1.txt > file1hash` and `sha256sum file2.txt > file2hash` to send each hash into its own new file using the `>` redirect operator.
- I used `cat file1hash` and `cat file2hash` to display the saved hashes. They were completely different, even though the files looked the same.
- I ran `cmp file1hash file2hash` to compare the two hash files byte by byte. It reported that they differ at the first byte on line 1, meaning the hashes didn't match from the very first character.

## Result

The two files looked identical with `cat`, but their SHA-256 hashes did not match, so file1.txt and file2.txt are not the same file. Something in them is different, even if it's too small to see (an extra space or one changed character, for example). This showed me that hashing is a reliable way to check data integrity, and that a hash comparison catches changes a visual check can miss.

## Key terms

- Hash function: an algorithm that turns data into a fixed-length code that can't be reversed or decrypted.
- Hash value (digest): the code a hash function produces; it acts as a unique fingerprint for a file's contents.
- SHA-256: the hash algorithm used here, producing a 256-bit value shown as 64 hex characters.
- Data integrity: confidence that data hasn't been changed or tampered with.
- sha256sum: Linux command that generates a SHA-256 hash for a file.
- cmp: Linux command that compares two files byte by byte and reports the first difference.
- `>` redirect: sends a command's output into a file instead of printing it to the screen.
- Why it matters: if a malicious program copies an original with even one line changed, its hash will be different, so security teams can spot the fake.
