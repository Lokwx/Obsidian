Assume that you have two 8-bit 2's complement numbers, a[7:0] and b[7:0]. These numbers are added to produce s[7:0]. Also compute whether a (signed) overflow has occurred.

### Solution

```
module top_module (
    input [7:0] a,
    input [7:0] b,
    output [7:0] s,
    output overflow
); //
 
    // assign s = ...
    // assign overflow = ...
    
    wire [8:0] carry;
    assign carry[0] = 0;
    assign overflow = carry[8] ^ carry[7];
    
    genvar i;
    generate 
        for (i = 0; i < 8; ++i) begin : loop
            fadd m1(a[i],b[i],carry[i],carry[i+1],s[i]);
        end
    endgenerate
    
endmodule

module fadd(input a, input b, input cin, output cout, output sum);
    assign {cout, sum} = a + b + cin;
endmodule
```


# Step 1. Unsigned numbers

Suppose you have **4 bits**.

Each bit has a value:

```
Bit:   3   2   1   0
Value: 8   4   2   1
```

Example:

```
0101

= 0×8 + 1×4 + 0×2 + 1×1
= 5
```

Another:

```
1111

= 8+4+2+1
=15
```

So 4-bit **unsigned** numbers go from

```
0000 = 0

...

1111 = 15
```

Easy.

---

# Step 2. But how do we store negative numbers?

Suppose we want

```
-1
-2
-3
```

We don't have a minus sign.

We only have 4 bits.

The solution computers use is called **two's complement**.

---

# Step 3. The leftmost bit becomes the sign bit

In 4 bits

```
Bit:   3   2   1   0
```

Bit 3 (the MSB) tells you whether the number is positive or negative.

The values become

```
Bit:   3    2   1   0
Value:-8    4   2   1
```

Notice something strange.

The leftmost bit is worth **-8**, not +8.

---

# Step 4. Examples

### Positive numbers

```
0001

= 1
```

```
0010

= 2
```

```
0111

= 4+2+1

=7
```

Exactly the same as unsigned.

---

### Negative numbers

Now look at

```
1000
```

Instead of

```
8
```

it means

```
-8
```

because

```
-8 +0+0+0

=-8
```

---

Another:

```
1001
```

equals

```
-8 +1

=-7
```

---

Another:

```
1110
```

equals

```
-8+4+2

=-2
```

---

Another:

```
1111
```

equals

```
-8+4+2+1

=-1
```

|Binary|Unsigned|Signed|
|---|---|---|
|0000|0|0|
|0001|1|1|
|0010|2|2|
|0011|3|3|
|0100|4|4|
|0101|5|5|
|0110|6|6|
|0111|7|7|
|1000|8|-8|
|1001|9|-7|
|1010|10|-6|
|1011|11|-5|
|1100|12|-4|
|1101|13|-3|
|1110|14|-2|
|1111|15|-1|
# Example 1: `+7 + +1`

```
   carry:  1 1 1 0
           ↓ ↓ ↓ ↓
           0 1 1 1
         + 0 0 0 1
         ----------
           1 0 0 0
```

Let's compute them one by one.

### Bit 0

```
1 + 1 = 10
```

- sum = 0
- carry = 1

So

```
c1 = 1
```

---

### Bit 1

```
1 + 0 + c1(=1)
= 10
```

- sum = 0
- carry = 1

```
c2 = 1
```

---

### Bit 2

```
1 + 0 + c2(=1)
=10
```

- sum = 0
- carry = 1

```
c3 = 1
```

---

### Bit 3 (MSB)

```
0 + 0 + c3(=1)
=1
```

- sum = 1
- carry = 0

```
c4 = 0
```

So the carries are

```
c0 c1 c2 c3 c4
0  1  1  1  0
         ↑  ↑
      into out
```

Overflow:

```
c3 ≠ c4
1 ≠ 0
```

✅ Overflow

Notice:

```
+7 + +1 = -8
```

Positive + Positive = Negative.

---

# Example 2: `+7 + (-7)`

Remember

```
-7 = 1001
```

Now add

```
           carry: 1 1 1 1
                  ↓ ↓ ↓ ↓
                  0 1 1 1
                + 1 0 0 1
                ----------
                  0 0 0 0
```

Compute them.

### Bit 0

```
1 + 1 =10
```

carry = 1

```
c1 =1
```

---

### Bit 1

```
1+0+1=10
```

carry =1

```
c2=1
```

---

### Bit 2

```
1+0+1=10
```

carry =1

```
c3=1
```

---

### Bit 3

```
0+1+1=10
```

sum=0

carry=1

```
c4=1
```

Carries become

```
c0 c1 c2 c3 c4
0  1  1  1  1
         ↑  ↑
      into out
```

Overflow?

```
1 XOR 1 = 0
```

❌ No overflow

Notice

```
+7 + (-7)=0
```

No sign problem.

---

# Example 3: `-8 + -8`

```
1000
1000
----
0000
```

Carries:

### Bit 0

```
0+0=0
```

```
c1=0
```

---

### Bit 1

```
0+0+0=0
```

```
c2=0
```

---

### Bit 2

```
0+0+0=0
```

```
c3=0
```

---

### Bit 3

```
1+1+0=10
```

sum=0

carry=1

```
c4=1
```

So

```
c0 c1 c2 c3 c4
0  0  0  0  1
         ↑  ↑
      into out
```

Overflow?

```
0 XOR 1 =1
```

✅ Overflow

Notice

```
-8 + -8
```

became

```
0000
```

which is positive.

Negative + Negative = Positive.

---

# Now compare all three

|Operation|Signs|`c3`|`c4`|Overflow|
|---|---|---|---|---|
|`0111 + 0001`|+ +|1|0|✅|
|`0111 + 1001`|+ −|1|1|❌|
|`1000 + 1000`|− −|0|1|✅|