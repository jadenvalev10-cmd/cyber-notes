# TryHackMe: Cryptography Concepts

Pre Security path, Attacks and Defenses module. October 2026.

**Situation:** Easy room (about 60 minutes) following The CIA Triad, on how cryptography protects confidentiality.

**Task:** Learn the core crypto terms, symmetric vs asymmetric encryption, and how real systems combine them.

**Action:**

- Introduction: plaintext (readable data), ciphertext (scrambled data), key (secret controlling encryption and decryption), algorithm (the public method).
- Symmetric encryption: one key for both encrypting and decrypting. Fast, but sharing the key is the weak point. Example: the Caesar cipher.
- Asymmetric encryption: a public key (shared with anyone) and a private key (kept by one owner). Solves key distribution and underpins the HTTPS handshake.
- Hybrid use: asymmetric encryption sets up a shared key, then symmetric encryption protects the data. This is what the browser padlock represents.
- Conclusion: cryptography is one layer of defence, alongside strong passwords, secure key storage, user awareness, updates, and monitoring.

**Result:** Worked through all sections of the room.

**Key terms**

plaintext, ciphertext, key, algorithm, symmetric encryption, asymmetric encryption, public key, private key, Caesar cipher, hybrid encryption
