## Substitution Cipher

**Plaintext** / **Ciphertext**: a string over a set of symbols U
$$
	U = \{\text{a,b,c,d .... }\}
$$
**Key**: A substitution table S, which represents a 1-1 onto function from U to U

![Pasted image 20260810202408](Pasted%20image%2020260810202408.png)

For example
$$
	a = g
$$
**Key Space**: Is the set of all possible keys
**Key Space Size / Size of Key Space**: total number of possible keys
**Key Size / Key Length**: number of bits required to represent a key

For a key space with 27 characters (a-z + _)
$$
	a \to z  = 26
$$
1) ==Key Space Size = 27! (Number of combinations)==
2) ==Key Length = approx 94 bits 

? Why 94 bits
With n bits, we can represent
$$
	2^n
$$
We want
$$
	2^n = 27!
$$
$$
	n = \log_{2} 27
$$
$$
	log_{2}​(27!)≈93.13
$$
We round up to get 94 bits

## Encryption

Given a plaintext 
$$
	X = x_{1}x_{2}x_{3}x_{4}x_{5}\dots xn
$$
and a key S

The output ciphertext (encrypted message) should be
$$
	E_{s} (X) = S(x_{1})S(x_{2})S(x_{3})\dots S(x_{n})
$$
Where 
$$
	E_{s}
$$
is the ciphertext obtained after converting each character in the plaintext using the encryption method with the key S.

## Decryption

Given a string of cipher text of length n
$$
	C = c_{1}c_{2}c_{3}\dots c_{4}
$$
Using the key, we can perform decryption which is the inverse process

$$
	D_{s}(C) = S^{-1}(C_{1})S^{-1}(C_{2})\dots

$$
---
Attacks on ciphers

### An attacker generally wants to either:
1) Find the key → Then can decrypt all ciphertext encrypted with that key
2) Learn plaintext information → May decrypt/learn something without ever finding the key

$$
	\text{Finding key} = \text{can obtain plaintext}
$$
$$
	\text{Obtaining plaintext information} \not \to  \text{Key might not be required to be found}
$$
### Information available to attacker
Before attacking, the attacker usually has some information
1) Many ciphertexts encrypted with the same key
2) Plaintext-ciphertext pairs
3) Other information depending on the attack model

### Attack Models
An Attack/Adversary model describes:
1. Attackers Capability → What information/access that they have
2. Attacker’s Goal → What they want to achieve

Attacker Capability

| Attack                   | Attacker Has                                                                 |
| ------------------------ | ---------------------------------------------------------------------------- |
| Ciphertext-only          | Ciphertexts                                                                  |
| Known Plaintext (KPA)    | Know cipher + plaintext pairs                                                |
| Chosen Plaintext (CPA)   | Can choose plaintext to be converted into the ciphertext (Encryption Oracle) |
| Chosen Ciphertext (CCA2) | Can choose ciphertext and the plaintext will be output (Decryption Oracle)   |
Attacker Goal

$$
	\text{Total Break} \to \text{Partial Break} \to \text{Distinguishability}
$$
Total break → Finding the secret key
Partial Break → Obtain some plaintext information without necessarily finding the key
Distinguishability (IND) → Distinguish which of two plaintexts a ciphertext corresponds to with a non random probability

---
Exhaustive Search
**Try every possible key until the correct one is found**
$$
	\text{Key Space} = 2^n
$$
For the substitution cipher
$$
	|K| = 27!
$$
Which is alot of keys to try
 ==A secure cipher should make exhaustive search computationally infeasible== 

---
Attack: known-plaintext-attack on substitution cipher

==A substitution cipher uses a fixed mapping==

$$
	a \to g, b \to v\dots
$$
Suppose attacker knows a pair, he can learn parts of the secret substitution table

Plaintext:   h e l l o _ w o r l d
Ciphertext:  h n l l q p o q i l b

He can recreate the mappings 

h → h
e → n
l → l
o → q
_ → p
w → o
r → i
d → b

So from **just one known plaintext-ciphertext pair**, the attacker has already recovered several entries of the key.

So from **just one known plaintext-ciphertext pair**, the attacker has already recovered several entries of the key.
 > No need to try all $27!$ keys — the plaintext/ciphertext pairs directly reveal the mapping.

---
Why is this a Known-Plaintext Attack (KPA)?

**KPA** means the attacker is given:

$$
	(m,c)
$$

where:
$m$ = known plaintext
$c$ = corresponding ciphertext

The attacker's goal here is to use those pairs to recover the **key**.

However, without knowing the plaintext it will be computationally intensive to find the plaintext using the ciphertext

Ciphertext-brute force
1) S = the set of all possible sub tables
2) For each key S → Decrypt the ciphertext, check whether the result looks like english
3) If it works, stop and use that as a key

**KPA doesn't mean the attacker chooses the plaintext**. They merely _already know_ some plaintexts and their corresponding ciphertexts. **CPA**, lets them _choose_ what gets encrypted.

---
Frequency Analysis Attack
==Substitution Cipher is vulnerable to *Frequency Analysis* attack==

If the attacker is aware that the plaintexts are English sentences, he could carry out the frequency analysis attack.

### Frequency Analysis Attack

**Frequency analysis** = use frequency patterns of plaintext language to infer the substitution key.

- English letters have predictable frequencies.
- Substitution changes symbols but **preserves frequency**.
- E.g. if `e → n`, high frequency of `e` becomes high frequency of `n`.
- Attacker compares ciphertext frequencies with expected English frequencies.
- Use guesses + word patterns to reconstruct more of the key.

> Substitution hides the letters, but not their statistical patterns.

==Can break substitution cipher much faster than exhaustive search of $27!$ keys.==

![Pasted image 20260810221114](Pasted%20image%2020260810221114.png)

