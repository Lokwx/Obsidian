Create 8 D flip-flops with active high synchronous reset. The flip-flops must be reset to 0x34 rather than zero. All DFFs should be triggered by the **negative** edge of clk.

```module top_module (
    input clk,
    input reset,
    input [7:0] d,
    output reg [7:0] q
);

    always @(negedge clk) begin
        if (reset) 
            q <= 8'h34; 
        else 
            q <= d;    
    end

endmodule
```

### Pointers
1. No need to separate the D-Flip Flops as u can just call them together and it will be a complete 8 D Flip Flop
