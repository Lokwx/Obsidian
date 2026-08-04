*Each product term in a SUM of products is called an implicant of the function*

For example
$$
	F(a,b,c) = \underbrace{ ab + a\overline bc + \overline a bc + \overline c + abc }_{ \text{ There are 5 implicants in this function } }
$$
## Prime implicants
- Implicant that cannot be combined with another term to eliminate a variable
- It cannot be enclosed within a larger square/rectangle in a K-map

For example
$$
	F = AB + ABC + BC
$$
In this case, we can see that ABC is already included in AB 

Why? 
$$
	AB = AB(1) \to AB(C + \overline C) = ABC + AB\overline C
$$
>This means that ABC in this statement is a implicant (*Not a prime implicant*)

## Essential Prime Implicants
- It is a prime implicant that is not included in any other prime implicant

For example
$$
	\overline AD  \cap B\overline D
$$

![Pasted image 20260804144717](Pasted%20image%2020260804144717.png)

> There is no complete overlap between any 2 implicants and they capture the most space
# Point of prime implicants
- They just want you to draw the biggest circle for the K-map
