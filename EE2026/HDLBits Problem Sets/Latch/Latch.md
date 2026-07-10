Implement the following circuit:

![Pasted image 20260710182559](Pasted%20image%2020260710182559.png)

Note that this is a latch, so a Quartus warning about having inferred a latch is expected.

- Latches are level-sensitive (not edge-sensitive) circuits, so in an always block, they use level-sensitive sensitivity lists.
- However, they are still sequential elements, so should use non-blocking assignments.
- A D-latch acts like a wire (or non-inverting buffer) when enabled, and preserves the current value when disabled.

```
module top_module (
    input d, 
    input ena,
    output reg q);

    always @(*) begin
        if (ena) q <= d;
    end
    
endmodule
```