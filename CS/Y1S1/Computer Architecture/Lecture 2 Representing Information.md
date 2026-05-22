---
notion-id: 281982ca-e761-8068-b9b7-d17e5c2720ce
---
Computers use binary 🤯

---

# Binary Coded Decimal

Takes a denary number and converts each digit into binary

Eg, 8192 = 1000 0001 1001 0010

---

# UTF-8

UTF uses variable length byte sequences unlike Unicode so that on average a character is shorter than 16 bits. UTF-8 is commonly used.

UTF-8 is called *self-synchronising* because you can always find the boundaries of characters by looking at the byte patterns, even if you start reading from the middle of a byte stream.

![[lecture-2-representing-information.png]]

- Top two bits tell us the type of byte

• Bit 7 is 0, a single byte character
• Bit 6-7 is 11, start of a MBCS, a leading byte
• Bit 6-7 is 10, part of a MBCS, a continuing byte

Here’s what that means:

- **Byte prefixes indicate roles**
    - The number of leading 1s indicates the number of bytes in the character
    - If the first bit is `0` → it’s a single-byte character (ASCII).
    - If the first bits are `110`, `1110`, or `11110` → it’s the first byte of a multi-byte character.
    - If the first bits are `10` → it’s a continuation byte.
- **Why this helps**
If you lose your place (e.g., you start in the middle of a string), you can scan forward or backward until you find a byte that *cannot* be a continuation byte (`10xxxxxx`). That must be the start of a character. From there, you can decode correctly again.
- **Practical effect**
This property makes it robust for things like stream processing, error recovery, substring searching, and random access, since you can regain synchronisation without needing to start from the very beginning.
