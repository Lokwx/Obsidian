Create 8 D flip-flops with active high synchronous reset. All DFFs should be triggered by the positive edge of clk.

```
module top_module (
    input clk,
    input reset,            // Synchronous reset
    input [7:0] d,
    output reg [7:0] q
);

    genvar i;
    generate
        for (i = 0; i < 8; ++i) begin : loop
            d m1(d[i],clk,reset,q[i]);
        end
    endgenerate
            
endmodule

module d(input d, input clk, input reset, output reg q);
    always @(posedge clk) begin
        if (reset) q <= 0;
        else q <= d;
    end
endmodule
```
