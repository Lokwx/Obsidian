### Check the MSB (Sign Bit) First

- **If the MSB is `0` (Positive):**
    
    - You **do not perform any complement operations**.
        
    - You read the number directly as a standard positive binary value.
        
    - _Example (4-bit 2's complement):_ `0101` $\rightarrow$ MSB is `0`, so it is simply $+5$.
        
- **If the MSB is `1` (Negative):**
    
    - The number is stored in complement form, so you **must perform the conversion process** to find its positive magnitude (and attach a minus sign).

### Converting a Negative Number Back to Decimal

If the MSB is `1`, you reverse the process according to whichever representation scheme is being used:

- **In 2's Complement:**
    
    - To decode `1101`: (Reapply 2’s complement again)
        
        1. Flip all bits: `0010`
            
        2. Add 1: `0010 + 1 = 0011` ($3$)
            
        3. Apply the minus sign $\rightarrow$ **$-3$**

- **In 1's Complement:**
    
    - To decode `1100`:
        
        1. Flip all bits: `0011` ($3$)
            
        2. Apply the minus sign $\rightarrow$ **$-3$**
            
- **In Signed Magnitude:**
    
    - To decode `1011`:
        
        1. Strip off the sign bit (`1` $\rightarrow$ negative)
            
        2. Read remaining bits: `011` ($3$)
            
        3. Apply the minus sign $\rightarrow$ **$-3$**

### 1. Representation of $+3$

Positive numbers are written directly in standard binary (with a `0` sign bit):

- **$+3 =$ `0011`**

### 2. Representation of $-3$

To get $-3$, you take the 1's complement of $+3$ (flip all bits):

- Flip `0011` $\rightarrow$ **`1100`**
    
- **$-3 =$ `1100`**

![Pasted image 20260803141529](Pasted%20image%2020260803141529.png)
> Do not need to convert (1) 00101100 → 00101100 using the reverse 2’s complement to get the magnitude as the sign for this result is 0, which indicates that the result is a positive number, can just read off the value which in this case is 44