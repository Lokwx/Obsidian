For each bit in an 8-bit vector, detect when the input signal changes from 0 in one clock cycle to 1 the next (similar to positive edge detection). The output bit should be set the cycle after a 0 to 1 transition occurs.

Here are some examples. For clarity, in[1] and pedge[1] are shown separately.

![Pasted image 20260710201542](Pasted%20image%2020260710201542.png)

```
module top_module (
    input clk,
    input [7:0] in,
    output reg [7:0] pedge
);
    reg [7:0] bfr = 8'b0;
    
    always @(posedge clk) begin
        bfr <= in;
        pedge <= in & ~bfr; 
    end
endmodule
```


### How the Math Handles it Independently

When your code executes `in & ~bfr`, it performs a **bitwise** operation. It aligns the bits vertically like this for Cycle 2:

```
   in:   1  0  0  0  0  0  0  0   (in[7] down to in[0])
& ~bfr:  1  1  1  1  1  1  1  1   (bfr was all 0, so inverted it is all 1)
-------------------------------
 pedge:  1  0  0  0  0  0  0  0   (Only pedge[7] fires!)
```

**Bitwise NOT (`~`) instead of Logical NOT (`!`)**

- **`!` (Logical NOT):** Converts the entire 8-bit vector into a single bit (`0` or `1`). If `bfr` is `8'b00000100`, `!bfr` evaluates to a single bit `0`.
    
- **`~` (Bitwise NOT):** Inverts every bit individually. If `bfr` is `8'b00000100`, `~bfr` cleanly evaluates to `8'b11111011`.
    
Since you are dealing with an 8-bit vector and need to detect edges for each bit independently, you must use the bitwise `~` operator.