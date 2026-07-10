Consider the sequential circuit below:

![Pasted image 20260710194700](Pasted%20image%2020260710194700.png)

```
module top_module (
	input clk,
	input L, //mux input
	input r_in,
	input q_in,
	output reg Q);
    
    wire D;
    
    always @(*) begin
        case (L)
            1'b0: D = q_in;
            1'b1: D = r_in;
        endcase
    end
    
    always @(posedge clk) begin
        Q <= D;
    end

endmodule
```