Achieving gate design using only NAND

<center>There are only 7 basic gates</center>
$$
	\begin{align}
	& OR  \\
	& NOR \\
	& AND \\
	& NAND \\
	& XOR \\
	& XNOR \\
	& NOT \\
	\end{align}
$$

For example given the following boolean equation
$$
	F = A\overline B + \overline C D

$$
Looking at the inputs, we know that these are the components that we need
$$
	\begin{align}
 & A\overline B \implies \text{1x NOT gate + 1x AND gate} \\
 & \text{This can be achieved using bubble pushing and NAND + NOT} \to AND \\
 & \overline CD \implies \text{1x NOT  gate + 1x AND gate} \\
 & \text{Similarly, this can be achieved using bubble pushing and NAND + NOT} \to AND \\ \\
 & A\overline B + \overline CD \implies \text{1x OR gate} \\
 & \text{This can be achieved using the intuition from Demorgans Law}. Where \\
 &  \\
 & A + B = \overline {\overline A \cdot \overline B} \\
 &  \\
 &  \text{This will give us the final result of F = } A\overline B + \overline C D
	\end{align}
$$

Another question could be

$$
	 F = (A + \overline B) \cdot (\overline C + D) \cdot E
$$
Looking at the individual components

$$
	A + \overline B \implies \text{1x NOT gate + 1x OR gate}
$$
$$
	\overline C + D \implies \text{1x NOT gate + 1x OR Gate}
$$
$$
	(A + \overline B) \cdot (\overline C + D) \cdot E \implies \text{1x 3 input AND Gate
	}
$$
However, we do not have a 3 input AND Gate (Assuming that we are using 2 input NAND gates in this exercise). 

We would need to cascade 2x AND gates and each AND gate can be found using the follow method

$$
	 {A \cdot B } \leftrightarrow \overline {\overline A \cdot \overline B}
$$
Then we would just cascade both inputs to achieve the following

$$
	\begin{align}
	&A -AND_{1.2}--- ||AND_{2.1}\\
	&B -AND_{1.2}--- ||AND_{2.1}\\
	&C ------- - |AND_{2.2}
	\end{align}
$$

>Can achieve the same results using the 3 gates as shown in the previous slide for NOR Gate Design


