## Similar Gates

$$
	A = \neg(\neg A)
$$

$$
\overline {A + B} \to \text{Applying Demorgans} \to \overline A \cdot \overline B
$$

$$
	\overline {A \cdot B} \to \text{Applying Demorgans} \to \overline A + \overline B
$$

## Not Gate Implementation using NAND/NOR

$$
	\overline  {A + A} \implies \overline {A \cdot A} \implies \overline A
$$

When A = 1

$$
	\overline {A + A} = \overline 1 = 0
$$

When A = 0

$$
	\overline {A + A} = \overline 0 = 1
$$

NAND gate achieves the same result as follows,

When A = 1

$$
	\overline {A + A} = \overline 1 = 0
$$

When A = 0

$$
	\overline {A + A} = \overline 0 = 1
$$

# Equivalent Logic Gates
> It is given that NAND and NOR gates are functionally complete → meaning that all 7 logic gates (incl itself) can be recreated using the same gates


## NAND

![Pasted image 20260804163623](Pasted%20image%2020260804163623.png)

Because AND uses both inputs (short circuit all inputs) it behaves as just a NOT gate

![Pasted image 20260804163659](Pasted%20image%2020260804163659.png)

- Bubble pushing method
	It behaves like a NAND gate, whereby the results is inverted
	Then u add in a NOT gate

$$
	NAND \to NOT \leftrightarrow AND
$$

AND

| A   | B   | F   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |

NAND

| A   | B   | F   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |


![Pasted image 20260804164114](Pasted%20image%2020260804164114.png)

To get OR, we start with Demorgans law

$$
	A + B \implies  \overline {\overline A \cdot \overline B}
$$

From this we can see that to get an OR, we just need to NOT both inputs first, followed by NAND it

$$
	\neg A \cdot \neg B \text{ followed by } \neg(\neg A \cdot \neg B) \implies A + B
$$

## NOR

Similarly we can achieve the same results as NAND using a bit of intuition from demorgans law

![Pasted image 20260804165304](Pasted%20image%2020260804165304.png)

Self explanatory

![Pasted image 20260804165318](Pasted%20image%2020260804165318.png)

Using demorgans law

$$
	A \cdot B = \overline {\overline A + \overline B}
$$

We can achieve this by $\neg$ the inputs, followed by using an NOR gate

![Pasted image 20260804165432](Pasted%20image%2020260804165432.png)

Self explanatory

$$
	A + B = \overline {\overline {A + B}}
$$
