# Why do we complement variables when finding maxterms?

The headers of the K-map show the **input values** for that row or column.

For example,

$$
\overline{A}B
$$

means the input is

$$
A=0,\qquad B=1.
$$

Suppose the value stored in that K-map cell is **0**. This means

$$
F(0,1)=0.
$$

To construct a **maxterm**, we need an **OR expression** that evaluates to **0** for this input.

Since an OR expression is **0 only if every literal is 0**, we choose each literal so that it evaluates to 0 under the given input.

- Since $A=0$, we write $A$, because $A=0$.
- Since $B=1$, we write $\overline{B}$, because $\overline{B}=0$.

Therefore, the maxterm is

$$
(A+\overline{B}).
$$

Substituting the input

$$
A=0,\qquad B=1
$$

gives

$$
A+\overline{B}
=0+0
=0.
$$

Thus, this maxterm is 0 exactly for the input

$$
(A,B)=(0,1).
$$

---

## General Rule

To construct a **maxterm**, the input values **do not change**. Instead, we choose each literal so that it evaluates to **0** for that input.

| Input value | Write in maxterm | Why? |
|--------------|------------------|------|
| $0$ | $A$ | Because $A=0$ |
| $1$ | $\overline{A}$ | Because $\overline{A}=0$ |

This is the opposite of a **minterm**, where every literal must evaluate to **1**.

| Input value | Write in minterm | Why? |
|--------------|------------------|------|
| $0$ | $\overline{A}$ | Because $\overline{A}=1$ |
| $1$ | $A$ | Because $A=1$ |

---
## How to get the resulting simplified values from the SOP Kmap

1) We will group the values with 0 together, similar to how we simplify a POS Kmap
2) As mentioned in the previous parts
$$
\text{For example: } { C\overline D  = 0 \to \overline C + D }
$$
	>We will take the complement of the 1’s and keep the value that is 0
	
3) Thereafter, we will $\cap$ the result together 

*There is no way to know if SOP is easier than POS*

