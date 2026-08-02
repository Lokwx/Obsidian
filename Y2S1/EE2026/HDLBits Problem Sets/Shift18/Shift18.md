Build a 64-bit _arithmetic_ shift register, with synchronous load. The shifter can shift both left and right, and by 1 or 8 bit positions, selected by amount.

An _arithmetic_ right shift shifts in the sign bit of the number in the shift register (q[63] in this case) instead of zero as done by a _logical_ right shift. Another way of thinking about an arithmetic right shift is that it assumes the number being shifted is signed and preserves the sign, so that arithmetic right shift divides a signed number by a power of two.

There is no difference between logical and arithmetic _left_ shifts.

- load: Loads shift register with data[63:0] instead of shifting.
- ena: Chooses whether to shift.
- amount: Chooses which direction and how much to shift.
    - 2'b00: shift left by 1 bit.
    - 2'b01: shift left by 8 bits.
    - 2'b10: shift right by 1 bit.
    - 2'b11: shift right by 8 bits.
- q: The contents of the shifter.


### The Cheat Code: The "Right-to-Left" Copy Trick

There is an even faster shortcut that requires zero math at all. If you want to find a negative number instantly, read the positive binary number from **right to left**:

1. Copy all bits exactly as they are **up to and including the first `1`**.
    
2. **Flip** all the remaining bits after that point.
    

Let's do $+4$ to $-4$ using this shortcut:

```
Positive 4:    0  0  0  0  0  1  0  0
                              ↑ 
                       (First 1 from the right)
```

1. Copy everything up to that first `1` exactly: `...100`
    
2. Flip all the remaining bits on the left: `11111100`
    

It gives you the exact same answer instantly with zero addition or subtraction.

#### 1. The Correct Way: Copy the Sign Bit (`1`)

If we copy the `1` into the new MSB spot, the top two bits both become `1`:

$$\text{Bits: } \mathbf{1 \ \ 1} \ \ 1 \ \ 1 \ \ 1 \ \ 1 \ \ 1 \ \ 0$$

$$\text{Weights: } (\mathbf{-128}) + (\mathbf{64}) + 32 + 16 + 8 + 4 + 2 + 0$$

Look at what those first two bits do together:

$$-128 + 64 = -64$$

By padding with a `1`, the combination of the new MSB and the shifted bit perfectly creates a new negative floor of **$-64$**. Because the floor dropped from $-128$ to $-64$, the entire value is cleanly divided by 2. The result evaluates to $-2$.

#### 2. The Broken Way: Padding with `0`

If you fill the empty spot with `0`, the top two bits become:

$$\text{Bits: } \mathbf{0 \ \ 1} \ \ 1 \ \ 1 \ \ 1 \ \ 1 \ \ 1 \ \ 0$$

$$\text{Weights: } (\mathbf{0}) + (\mathbf{64}) + 32 + 16 + 8 + 4 + 2 + 0$$

Your negative floor is completely gone. Instead of a negative base, you just have a massive positive floor of $+64$, turning the whole number into $+126$.

## **An arithmetic right shift copies the sign bit because it keeps the MSB active, which mathematically shrinks the negative floor proportionally alongside the positive bits, keeping the division accurate.**

```
module top_module(
    input clk,
    input load,
    input ena,
    input [1:0] amount,
    input [63:0] data,
    output reg [63:0] q); 

    always @(posedge clk) begin
        if (load) q <= data;
        else if (ena) begin 
            case(amount)
                2'b00: q <= {q[62:0],1'b0};
                2'b01: q <= {q[63-8:0],{8{1'b0}}};
                2'b10: q <= {q[63],q[63:1]};
                2'b11: q <= {{8{q[63]}},q[63:0+8]};
            endcase
        end
    end
    
endmodule
```

### Pointers
1. Concat must have size for input values e.g. 0,1 if not got error