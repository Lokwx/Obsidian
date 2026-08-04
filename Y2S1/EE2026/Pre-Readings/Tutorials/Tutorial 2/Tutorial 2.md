operator - (NOT) on single operand
operators ∙ (AND), + (OR) on multiple operands 
> ⋅ has precedence over +

There exists a 0 and 1 element in B, such that 
- x+0 = x 
	> Combining any element x with 0 using the + operation leaves x completely unchanged (Do nothing)
	
- x . 1 = x
	>Multiplying any element x with 1 will not change the result

Commutative Law
- x + y = y + x
	>Self explanatory
- x\*y = y\*x
	>Order doesn’t matter


![Pasted image 20260803111620](Pasted%20image%2020260803111620.png)


- **Expand the right side:**

    $$

(x + y)(x + z) = x \cdot x + x \cdot z + y \cdot x + y \cdot z

$$
    
- **Apply Idempotent Law ($x \cdot x = x$):**
    
    $$
= x + xz + xy + yz
$$

- **Factor out $x$ from the first terms (Absorption Law, $x + xz = x$):**

    $$

= x(1 + z + y) + yz

$$
    
- **Apply Boundedness Law ($1 + \text{anything} = 1$):**
    
    $$
= x(1) + yz
$$

- **Apply Identity Law ($x \cdot 1 = x$):**

    $$

= x + yz \quad \text{(Matches the left-hand side)}

$$

![Pasted image 20260803112556](Pasted%20image%2020260803112556.png)

1) 1 OR 0 → 1
2) 1 and 0 → 0

---

![Pasted image 20260803112635](Pasted%20image%2020260803112635.png)

---

![Pasted image 20260803112756](Pasted%20image%2020260803112756.png)


Dont look at + and \* as addition or multiplication
> Look at it as like OR and AND then it will make much more sense

