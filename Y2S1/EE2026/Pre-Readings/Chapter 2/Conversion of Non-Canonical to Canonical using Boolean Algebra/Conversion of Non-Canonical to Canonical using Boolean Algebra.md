![Pasted image 20260803220042](Pasted%20image%2020260803220042.png)

To compute canonical SOP using boolean algebra, we can use 
$$
	\text{Postulates: } (A + \overline A) = 1
$$
$$
	\text{Identity Law: } A \cdot 1 = A
$$
For union law, we can see that by $\cdot 1$ we do not change the initial part because A AND 1 will always depend on A

Using these properties, we can form canonical SOPs

$$
\begin{align}
&\text{For example,} \\
&\overline xy + xz \\
&\overline xy \cdot 1 + x\cdot 1\cdot z \\
&\overline xy(z + \overline z) + x\cdot(\overline y + y)\cdot z \\ \\
&\text{By expanding, we will get the result} \\
&\overline xyz + \overline x\overline y z + x\overline yz + xyz 
\end{align}	
$$

Alternatively,
$$
\begin{align*}
&\text{Given } \bar{x}y + xz \\
&\text{We apply De Morgan's law as follows:} \\
&\overline{\overline{\bar{x}y + xz}} \leftarrow \text{Complement twice (same result)} \\[1em]
&\text{De Morgan says that } \overline{A+B} = \bar{A} \cdot \bar{B} \\
&\therefore \overline{\bar{x}y} \cdot \overline{xz} \\[1em]
&\text{Applying De Morgan's to the first part:} \\
&\overline{\bar{x}y} = \overline{\bar{x}} + \bar{y} = x + \bar{y} \\[1em]
&\text{Applying De Morgan's to the other part:} \\
&\overline{xz} = \bar{x} + \bar{z} \\[1em]
&\text{Combining those two together, we get:} \\
&(x+\bar{y}) \cdot (\bar{x} + \bar{z}) \\[1em]
&\text{Using expansion, we get the CPOS that we want.}
\end{align*}
$$



