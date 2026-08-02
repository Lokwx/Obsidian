Implement the following circuit:

![Pasted image 20260710182647](Pasted%20image%2020260710182647.png)

```
module top_module (
    input clk,
    input d, 
    input ar,   // asynchronous reset
    output reg q);

    always @(posedge clk or posedge ar) begin
        if (ar) q <= 0;
        else if (clk) q <= d;
    end
    
endmodule
```

### For DFF
1. Ensure that the always sensitivity list captures the edges correctly and not miss out any, for normal latches, its level sensitive so you need to be aware

|D Latch|D Flip-Flop (DFF)|
|---|---|
|**Level-sensitive**|**Edge-triggered**|
|Output follows `d` whenever `ena` is high|Output changes only on the clock edge|
|Uses an enable (`ena`)|Uses a clock (`clk`)|
|Can change multiple times while enabled|Changes at most once per clock edge|
A latch is **level-sensitive**, so it is typically written as combinational logic (`always @(*)`) with an incomplete assignment that causes synthesis to infer storage. The asynchronous reset is simply another condition with highest priority; there is no need for `posedge ar` because the block is reevaluated whenever `ar` changes.