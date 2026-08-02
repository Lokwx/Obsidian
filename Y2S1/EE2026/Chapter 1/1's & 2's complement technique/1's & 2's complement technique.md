#complement
Diminished-Radix Complement Representation (Radix - 1) → 1’s complement 
Radix Complement → 2’s Complement

![Pasted image 20260802184309](Pasted%20image%2020260802184309.png)

1st complement → Use the maximum value for the radix (e.g for radix r = 2), where the values range from (0 - 2^(n-1)) → (0 - 1) 
So in this case, the maximum value is 1

To get the 1’s complement, simply subtract the subtrahend by the max val (equal digits)
```
	1111
-   1011
  --------
    0100
```

![Pasted image 20260802183856](Pasted%20image%2020260802183856.png)

The carry signifies that the minuend (magnitude) is greater than the subtrahend (magnitude)
- Thats why we need the End Around Carry, if there is *any* to add to the final result that we get from the result

### 2’s complement
Add 1 to the 1’s complement

![Pasted image 20260802184740](Pasted%20image%2020260802184740.png)

For 2’s complement, you do not need to use end around carry

![Pasted image 20260802185137](Pasted%20image%2020260802185137.png)

can just ignore the carry for 2’s complement


When your technique is the **Radix Complement** ($r$'s complement, such as 2's complement in binary or 10's complement in decimal), you **discard** the end-around carry. You only perform the "end-around carry" (adding it back to the end) when using the **Diminished-Radix Complement** ($r-1$'s complement, like 1's complement or 9's complement).

### Quick Comparison

|**Complement Type**|**Binary Ex.**|**Decimal Ex.**|**What to do with the extra carry?**|
|---|---|---|---|
|**Diminished-Radix** ($r - 1$)|1's Complement|9's Complement|**Add it to the back** (End-Around Carry)|
|**Radix** ($r$)|2's Complement|10's Complement|**DISCARD IT** (Ignore it)|
- When you use the **$(r-1)$'s complement**, you are off by $-1$, so the extra end carry has to be wrapped back around and **added to the answer** to fix the offset.
    
- When you use the **$r$'s complement**, that $+1$ was already baked into your number from the start! The end carry simply represents an overflow of $r^n$, so you **drop it**.

### Converting diminished radix form back into an original form
> If you are using diminished radix complement, but you do not get a end around carry, it means that the top value is smaller than the bottom value and you should have a negative number

e.g. 1 - 3

```
3 (11)
1's complement of 3
 11
-00
 00
 
using addition (1 + (-3))
1 (01)

 01
+00
 01
 
 *There is no end around carry*
 
 convert 01 back to 1's complement
  11
 -01
  10
  
  = 2 (negative because there is no end around carry)
```