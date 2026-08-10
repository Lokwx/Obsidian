## Symmetric encryption scheme/Cipher
> A process that consists of 2 algorithms: *Encryption and decryption*
## Plaintext
> File to be encrypted

## Encryption
> An algorithm that encrypts a plaintext/file

# Correctness
> For any plaintext x and key k

$$
	D_{k} (E_{k}(x)) = x
$$
This means that using the decryption method, it cancels out the encryption method and returns the plaintext (x)

# Security
> From the ciphertext, it is “difficult” to derive useful information of the key k and the plaintext x. 
> To someone who doesn’t know the key, the ciphertext resembles sequences of random bytes


## Examples
- Alice encrypts her file using Winzip which uses AES (a type of standard encryption scheme) using a secret password (k) which is also the encryption key
- She sends the secret password through a secure channel to Bob 
- She then sends the ciphertext via a public channel. The data might be eavesdropped. 
- Bob receives the ciphertext and he is able to get the plaintext with the encryption key

> 	Even though Bob is able to decrypt the ciphertext into the plaintext using the encryption key, someone like Eve who is reading the ciphertext will see the ciphertext as just string of random bytes (similar to a random string)


# Cryptography (cryptology)
1) Is the study of techniques in securing communication
2) Encryption is one of the primitives in cryptography

### Common Placeholders
1) Alice (Origin)
2) Bob (Receiver)
3) Eve (Eavsedropper)

# Security Models
- Categorize security achieved by an encryption by describing the events/class of attacks it can prevent

## Attack Model/Adversary Model
*An attack can be described as*
1) Attackers knowledge (information available)
2) Computing resources
3) Attackers goal
4) *Attack model are applications dependent*

### Information

Suppose Alice uses the same secret key to encrypt many messages

### Ciphertext-only attack
1. The attacker has only the ciphertext (no plaintext)
2. The attacker *might* know some properties about the plaintext (e.g. if the plaintext is an english sentence)

### Known-plaintext attack
1. The attacker already knows some encryption pairs
$$
	\text{"Hello"} \to \text{X7AF2}
$$
$$
	\text{"Goodbye"} \to \text{P3K91}
$$
When he receives a ciphertext e.g
$$
	\text{"Q9BZ1"} \to \text{"?"}
$$
He might be able to reverse engineer the ciphertext if he has enough encryption pairs
*Known plaintext is information used to help attack other encrypted data*

### Chosen-plaintext attack (CPA)
- The attacker has access to a blackbox (Encryption oracle). 
#### Encryption Oracle 
Allows the attacker to generate as many ciphertext as he wants using different plaintext that he feeds in (using the same key). 

The goal is to use what they learn from their queries to attack the target.
### Chosen ciphertext attack (CCA2)
The attacker has a decryption oracle

### CPA

You have a machine that **encrypts things for you**.

You give it:  
`HELLO`

It gives you:  
`X7A91`

So:

**CPA = “Encrypt this for me.”**

---

### CCA1

You have a machine that **decrypts things for you**.

You can use it **before** you receive the secret ciphertext.

```
You: decrypt ABC
Machine: "HELLO"

You: decrypt XYZ
Machine: "GOODBYE"

--- Now you receive the target 🔒 ---

Target: QWE123 = ???

❌ Machine is taken away
```

Now you have to figure out the target yourself.

**CCA1 = “I can decrypt stuff BEFORE getting the target.”**

---

### CCA2

Same thing, except the machine **is NOT taken away**.

```
You: decrypt ABC
Machine: "HELLO"

--- You receive the target 🔒 ---

Target: QWE123 = ???

You: decrypt XYZ
Machine: "GOODBYE"

You: decrypt ASD
Machine: "PASSWORD"

✅ You can keep using the machine
```

But there's one rule:

```
You: decrypt QWE123 ← the actual target

Machine: ❌ NO
```

Because otherwise you'd instantly win.

**CCA2 = “I can decrypt stuff BEFORE AND AFTER getting the target.”**

---
## Goals

### Total break
> When an attacker wants to find the keys

### Partial Break
*The definitions may vary*, but
1) Decryption of a cyphertext
2) Determine some coarse information about the plaintext (e.g. whether the plaintext is a jpeg image or a c program)

### Indistinguishability (IND)
An attacker does not need to completely decrypt a ciphertext for an attack to be useful.

For example, suppose that the plaintext can be either 
$$
	\text{Y = Yes}
$$
$$
	\text{N = No}
$$
The attacker might not know how to decrypt ciphertexts. However, if they can look at a cipher text and determine whether it encrypts Y or N with a probability meaningfully better than random guessing, they have learned information,

$$
	\text{P(Correct Guess)} = \frac{1}{2}
$$
For the attacker to break indistinguishability, 
$$
	\text{P(Correct Guess)} = \frac{1}{2} + e
$$
This means that the encryption scheme failed at encrypting different plaintexts

---

