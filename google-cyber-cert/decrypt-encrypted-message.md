# Decrypt an Encrypted Message

Google Cybersecurity Certificate activity

## Situation

I was working as a security analyst in a Linux lab environment where every file in my home directory had been encrypted. I started as the user analyst in /home/analyst, which held two files (Q1.encrypted and README.txt) and a subdirectory called caesar. To get my data back, I had to find a hidden file, break the Caesar cipher protecting it, and use what it revealed to decrypt the main data file.

## Task

Use Linux commands to explore the directory, find a hidden file, decrypt the Caesar cipher inside it, and then decrypt the encrypted data file to read the hidden message.

## Action

- I ran `ls` in the home directory to list the files, then used `cat README.txt` to read the instructions. The message said the caesar subdirectory contained a hidden file.
- I moved into the subdirectory with `cd caesar` and ran `ls -a` to list all files, including hidden ones. Hidden files in Linux start with a period, which is how I found `.leftShift3`.
- I read the file with `cat .leftShift3` and the text was scrambled because it was encrypted with a Caesar cipher. The file name hinted at the key: each letter was shifted three places to the left, so d stands for a, e stands for b, and so on.
- I decrypted it with `tr "d-za-cD-ZA-C" "a-zA-Z"`, piping the file into it. The `tr` command translates characters from one set to another: the first set (d-za-cD-ZA-C) is the shifted alphabet and the second (a-zA-Z) is the normal alphabet, so every letter gets mapped back to where it started. The readable output gave me the command for the next task.
- I went back to the home directory with `cd ..` and ran the `openssl` command the hidden file revealed to decrypt `Q1.encrypted`. It used AES-256-CBC with `-pbkdf2`, `-a`, `-d`, `-in` for the input file, `-out` for the output file, and `-k` for the password, which the lab provided.
- I ran `ls` again and saw the new file `Q1.recovered`, then used `cat Q1.recovered` to read the decrypted message.

## Result

I recovered the data and read the hidden message. The lab showed two layers of protection: a weak, old Caesar cipher that I could break just by reversing the shift, and a much stronger AES-256 symmetric encryption that only opened once I had the correct password. It also reinforced that hidden files are easy to find with ls -a, so hiding something is not the same as securing it.

## Key terms

- **Encryption:** converting readable data (plaintext) into unreadable data (ciphertext) so only people with the key can read it.
- **Decryption:** reversing encryption to turn ciphertext back into plaintext.
- **Caesar cipher:** one of the earliest ciphers; every letter is shifted a fixed number of places in the alphabet, which makes it easy to break.
- **Symmetric encryption:** the same key is used to encrypt and decrypt.
- **AES-256-CBC:** a secure symmetric cipher (256-bit AES in cipher block chaining mode).
- **PBKDF2:** a method that strengthens a password-based key, which adds security against guessing.
- **Hidden file:** a Linux file whose name starts with a period; it shows up with ls -a.
- **tr:** a command that translates one set of characters to another.
- **openssl:** a command-line tool for cryptographic tasks, used here to decrypt a file.
