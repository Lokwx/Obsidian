Build a counter that counts from 0 to 999, inclusive, with a period of 1000 cycles. The reset input is synchronous, and should reset the counter to 0.

![Pasted image 20260801213440](Pasted%20image%2020260801213440.png)


```
module top_module (
    input clk,
    input reset,
    output [9:0] q);

    always @(posedge clk) begin
        if (reset) q <= 0;
        else q <= (q+1)%1000;
    end
    
endmodule

```