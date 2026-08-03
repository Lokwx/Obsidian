![Pasted image 20260803220042](Pasted%20image%2020260803220042.png)

TTo compute canonical SOP (CSOP) using Boolean algebra, we use the **Complement Law** ($A + \bar{A} = 1$) and the **Identity Law** ($A \cdot 1 = A$). Multiplying by $1$ does not change the function value, as $A \cdot 1 = A$.

Using these properties, we can convert SOP to CSOP:

$$
\begin{align*}
&\text{Given: } \bar{x}y + xz \\
&= \bar{x}y \cdot 1 + x \cdot 1 \cdot z \\
&= \bar{x}y(z + \bar{z}) + x(y + \bar{y})z \\
&= \bar{x}yz + \bar{x}y\bar{z} + xyz + x\bar{y}z
\end{align*}
$$

---

### Alternative Method: Converting SOP to CPOS

$$
\begin{align*}
&\text{Given: } \bar{x}y + xz \\
&\text{We apply De Morgan's law as follows:} \\
&\overline{\overline{\bar{x}y + xz}} \leftarrow \text{Complement twice (same result)} \\[1em]
&\text{De Morgan's Theorem: } \overline{A+B} = \bar{A} \cdot \bar{B} \\
&\therefore \overline{\bar{x}y} \cdot \overline{xz} \\[1em]
&\text{Applying De Morgan's to the first term:} \\
&\overline{\bar{x}y} = \overline{\bar{x}} + \bar{y} = x + \bar{y} \\[1em]
&\text{Applying De Morgan's to the second term:} \\
&\overline{xz} = \bar{x} + \bar{z} \\[1em]
&\text{Combining the terms yields POS form:} \\
&(x + \bar{y}) \cdot (\bar{x} + \bar{z}) \\[1em]
&\text{Next step: Expand using the distribution postulate to reach CPOS.}
\end{align*}
$$



