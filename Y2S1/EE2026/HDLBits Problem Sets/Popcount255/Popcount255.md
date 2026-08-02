#forloops

A "population count" circuit counts the number of '1's in an input vector. Build a population count circuit for a 255-bit input vector.

### Solution

```
module top_module( 
    input [254:0] in,
    output [7:0] out );

    always_comb begin
        out = 8'b0;
        for (int i = 0; i < 255; ++i) begin
            if (in[i] == 1'b1) out = out + 1'b1;
        end
    end
endmodule
```

### Pointers
1. Do not use ++out, it can only be used for **for loops**, use normal bit addition instead