You are provided with a BCD (binary-coded decimal) one-digit adder named bcd_fadd that adds two BCD digits and carry-in, and produces a sum and carry-out.

```
module bcd_fadd (
    input [3:0] a,
    input [3:0] b,
    input     cin,
    output   cout,
    output [3:0] sum );
```

Instantiate 4 copies of bcd_fadd to create a 4-digit BCD ripple-carry adder. Your adder should add two 4-digit BCD numbers (packed into 16-bit vectors) and a carry-in to produce a 4-digit sum and carry out.

### Solution

```
module top_module ( 
    input [15:0] a, b,
    input cin,
    output cout,
    output [15:0] sum );
    
    wire [4:0] carry;
    assign carry[0] = cin;
    assign cout = carry[4];

    genvar i;
    generate 
        for (i = 0; i < 16; i = i + 4) begin : loop
            bcd_fadd m1(a[i+:4],b[i+:4],carry[i/4],carry[i/4+1],sum[i+:4]);
        end
    endgenerate
    
endmodule
```

## Full adder vs BCD adder

### A normal full adder (`fadd`)

Adds **1 bit**:

```
a + b + cin
```

For example:

```
1 + 1 + 0 = 10₂

sum  = 0
cout = 1
```


### A BCD full adder (`bcd_fadd`)

Adds **one decimal digit (4 bits)**:

```
a[3:0] + b[3:0] + cin
```

Internally, it might look something like this:

```
          4-bit Ripple Adder
      ┌────────────────────────┐
a ----│                        │
b ----│ 4 × binary full adders │----> temp_sum
cin --│                        │----> temp_carry
      └────────────────────────┘
                  │
                  ▼
      Is temp_sum > 9 or carry?
                  │
          Yes ────┴──── No
           │
           ▼
      Add 0110 (decimal 6)
           │
           ▼
      Correct BCD sum & carry
```

So a `bcd_fadd` is **more than just 4 full adders**.

### Example: 5 + 4

```
0101
0100
----
1001
```

`1001` is decimal 9, which is already a valid BCD digit.

So no correction is needed.

---

### Example: 7 + 8

```
0111
1000
----
1111   (binary 15)
```

`1111` is **not** a valid BCD digit.

The BCD adder detects this and adds 6:

```
1111
0110
----
1 0101
```

Result:

```
carry = 1
sum   = 0101
```

which represents decimal **15**.

A plain 4-bit ripple-carry adder **cannot** do this correction by itself.

## Step 1: Perform normal 4-bit binary addition

Suppose you want to add:

```
7 + 8
```

In binary:

```
  0111   (7)
+ 1000   (8)
+    0   (cin)
-------
  1111   (15)
```

A normal 4-bit ripple-carry adder gives:

```
temp_sum   = 1111
temp_cout  = 0
```

---

## Step 2: Check if the result is a valid BCD digit

A BCD digit can only be

```
0000 = 0
...
1001 = 9
```

Anything from

```
1010 (10)
to
1111 (15)
```

is invalid.

So the correction condition is:

```
if (temp_cout == 1 || temp_sum > 9)
```

or more commonly written as

```
correction = temp_cout | (temp_sum > 4'd9);
```

temp_cout → The carry digit when 2 bcd are added
temp_sum → the  sum when 2 bcd are added (must be within 0-9)

## Step 3: Add 6 (0110) if correction is needed

Why **6**?

Because after binary 9:

```
1001 = 9
1010 = 10  ❌
1011 = 11  ❌
1100 = 12  ❌
1101 = 13  ❌
1110 = 14  ❌
1111 = 15  ❌
```

Adding `0110` shifts these invalid values into the correct BCD representation.

Example:

```
1111   (15)
0110
------
1 0101
```

Result:

```
carry = 1
digit = 0101 (5)
```

which means

```
15 = 1 5
```

Exactly what we want.

---

## Another example: 9 + 9

Binary addition:

```
1001
1001
----
10010
```

So

```
temp_sum  = 0010
temp_cout = 1
```

Since there is a carry, correction is needed.

Add 6:

```
0010
0110
----
1000
```

Keep the carry:

```
carry = 1
sum   = 1000 (8)
```

Result:

```
18
```

which is correct.

```
wire [4:0] temp; wire [4:0] corrected; assign temp = a + b + cin; assign corrected = (temp > 5'd9) ? temp + 5'd6 : temp; assign sum = corrected[3:0]; assign cout = corrected[4];
```

### Intutition
## Why specifically 6?

Look at the gap between binary and BCD.

Binary after 9:

```
Decimal   Binary
9         1001
10        1010
11        1011
12        1100
13        1101
14        1110
15        1111
```

BCD after 9:

```
Decimal   BCD
9         1001
10        0001 0000
11        0001 0001
12        0001 0010
13        0001 0011
14        0001 0100
15        0001 0101
```

To get from the binary representation to the correct BCD representation, you need to "skip over" the six invalid patterns (`1010` through `1111`). Adding `0110` does exactly that.

e.g. if 13 + 6, you are skipping 14,15 → wrap → 0,1,2,3 
= (0001) [1] (0011) [3]