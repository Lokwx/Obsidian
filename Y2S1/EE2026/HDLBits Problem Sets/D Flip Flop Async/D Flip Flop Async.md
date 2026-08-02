Async does not follow the clock cycle, by putting it inside the sensitivity list, whenever the async reset changes state (0 → 1) posedge areset, the if else statements will run which will reset it.

```
module top_module (
    input clk,
    input areset,   // active high asynchronous reset
    input [7:0] d,
    output [7:0] q
);

    always @(posedge clk or posedge areset) begin 
        if (areset) q <= 0;
        else q <= d;
    end
    
endmodule
```
