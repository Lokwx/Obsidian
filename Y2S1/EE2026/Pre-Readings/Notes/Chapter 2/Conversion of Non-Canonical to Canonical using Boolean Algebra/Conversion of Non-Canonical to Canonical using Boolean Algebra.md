![[Pasted image 20260803220042.png]]

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
\begin{align}
&\text{Given } \overline xy + xz  \\
&\text{We apply demorgans law as follows,} \\ 
& \overline {\overline {\overline xy + xz}} \leftarrow \text{Complement twice (same result)}\\
&  \\
& \text{Demorgan says that } \overline{A+B} = \overline A\cdot \overline B &  \\
& \therefore \overline{\overline xy} \cdot \overline{xz} \\
&  \\
& \text{Applying demorgans to the first part} \\
& \overline {\overline x y} = \overline {\overline x} + \overline y = x + \overline y \\
&  \\
& \text{Applying demorgans to the other part} \\
& \overline {xz} = \overline x + \overline z \\
&  \\
& \text{Combining those two together, we will get} \\
& (x+\overline y)\cdot(\overline x + \overline z) \\
&  \\
& \text{Using expansion, we will get the CPOS that we want which is long so i wont type it out}
\end{align}
$$