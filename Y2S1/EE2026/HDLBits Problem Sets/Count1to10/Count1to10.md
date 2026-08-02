Make a decade counter that counts 1 through 10, inclusive. The reset input is synchronous, and should reset the counter to 1.

![Pasted image 20260711141221](Pasted%20image%2020260711141221.png)

```
module top_module (
    input clk,
    input reset,
    output [3:0] q);

    always @(posedge clk) begin
        if (reset) q <= 1'b1;
        else begin 
            if (q == 4'd10) q <= 1'b1;
            else q <= q + 1'b1;
        end
    end 
    
endmodule
```