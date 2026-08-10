## Substitution Cipher

## Permutation Cipher
- Known as the transposition cipher

Unlike a **substitution cipher**, we do **not replace characters**.

Instead:

> **Permutation cipher = keep the same characters, but shuffle their positions.**

For example:

t=5

So split the plaintext into groups of **5 characters**:

```
ABCDE | FGHIJ | KLMNO | ...
```

Then use the same secret permutation on **every block**.

The example key is:

p=(1,5,2,4,3)

This means:

|Original position $i$|Moves to position $p_i$|
|---|---|
|1|1|
|2|5|
|3|2|
|4|4|
|5|3|
So for:

```
Position:    1  2  3  4  5
Plaintext:   A  B  C  D  E
```

move each character:

```
A: 1 → 1
B: 2 → 5
C: 3 → 2
D: 4 → 4
E: 5 → 3
```

giving:

```
Ciphertext:  A  C  E  D  B
```

---

Cryptanalysis (known-plaintext attack)

## Why is Known-Plaintext Attack easy?

Suppose Eve knows:

```
Plaintext:   A B C D E
Ciphertext:  A C E D B
```

She can simply compare positions:

```
A moved 1 → 1
B moved 2 → 5
C moved 3 → 2
D moved 4 → 4
E moved 5 → 3
```

Therefore she immediately obtains:

p=(1,5,2,4,3)​

![](2022_CS2107_Lecture_1.pdf#page=24&rect=29,173,632,326)

We can see that the ciphertext repeats 

**Finding block size $t$ (KPA):**
1. Try possible block sizes.
2. Compare plaintext ↔ ciphertext positions.
3. Find where the same positional permutation repeats for every block.
4. That repeating length is likely $t$.

> $t$ = period/length of the repeating shuffle.

Try possible block sizes and check the character count before finding the key which comprises of t (block size) and p (permutation)

### Try $t=3$

```
m: aab | bbb | aba | baa
c: bab | aab | bba | baa
```

Look at block 2:

```
m: bbb
c: aab
```

Impossible — rearranging `bbb` can never produce `aab`.

So:
### Try $t=4$

```
m: aabb | bbab | abaa
c: baba | abbb | abaa
```

Check character counts:

```
aabb ↔ baba   ✓ 2a, 2b
bbab ↔ abbb   ✓ 1a, 3b
abaa ↔ abaa   ✓ 3a, 1b
```

![](2022_CS2107_Lecture_1.pdf#page=25&rect=27,166,624,346)

---
One Time Pad
![](2022_CS2107_Lecture_1.pdf#page=26&rect=46,5,704,282)



