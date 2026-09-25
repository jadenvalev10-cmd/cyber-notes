# TryHackMe: Data Encoding

Pre Security path, Software Basics module (Easy, ~45 min). Completed.

The room covers how computers encode characters as bits: ASCII, its 8-bit regional extensions (the ISO-8859 series), and Unicode with UTF-8, UTF-16, and UTF-32.

## Task 1: Introduction

Frames the topic: how does a computer turn 0s and 1s into readable text?

## Task 2: ASCII

- ASCII (American Standard Code for Information Interchange, 1963) is a 7-bit standard (0-127) covering English letters, digits, punctuation, and control characters.
- Letters and digits are sequential (e.g. a = 61, b = 62, c = 63 in hex), so you can derive neighboring characters from one known code.
- **Worked example:** "TryHackMe" in ASCII binary is `01010100 01110010 01111001 01001000 01100001 01100011 01101011 01001101 01100101 00001010` (it ends with `\n`). In hex: `54 72 79 48 61 63 6b 4d 65 0a`.
- ASCII's 7 bits could not cover accented or non-English letters. Using an 8th bit, the ISO/IEC 8859 series added regional variants:
  - ISO-8859-1 (Latin-1): German, French, Spanish, Italian, Portuguese, Nordic
  - ISO-8859-2 (Latin-2): Polish, Czech, Hungarian, Croatian, Romanian, Slovak
- A document saved in one and read in the other displays wrong or garbled characters.

## Task 3: Unicode

**Why ASCII and extended ASCII don't scale:**

- Arabic needs 250+ characters for ligatures and diacritics.
- Japanese has 2,136+ daily-use Kanji (JIS X 0208 defines 6,879).
- Chinese GB 18030-2022 defines 87,887+ Hanzi.
- All of this is before even counting emoji.

**Unicode:**

- A universal character encoding standard that assigns a unique **code point** to every character across all writing systems, so sender and recipient never need to agree on a regional encoding.
- Unicode 17.0 defines about 157,000 characters, about 4,000 of them emoji.
- Example code points: `U+0041` = Latin "A", `U+03A9` = Greek "Ω", `U+3042` = Japanese Hiragana "あ".

**Encodings:**

- **UTF-8:** variable length, 1-4 bytes per code point. ASCII characters (`U+0000` to `U+007F`) stay 1 byte (backward compatible), non-ASCII characters like Ω use 2 bytes, and emoji like 🔥 use 4 bytes. It is the most common encoding on the modern web.
- **UTF-16:** 2 or 4 bytes per character. Common scripts (Latin, Cyrillic, Chinese Hanzi) fit in 2 bytes; rarer ones (emoji, ancient scripts) need a surrogate pair of two 16-bit units (4 bytes total). For example, 🔥 = `U+D83D U+DD25`.
- **UTF-32:** a fixed 4 bytes per code point, always. Simplest but most wasteful (e.g. A = `U+00000041`).

## Task 4: Conclusion

Recap: ASCII's limits, why regional 8-bit extensions caused encoding mismatches, and how Unicode plus UTF-8, UTF-16, and UTF-32 solved cross-language text representation. The follow-up room is Python: Simple Demo, which shows computers manipulating this data directly.
