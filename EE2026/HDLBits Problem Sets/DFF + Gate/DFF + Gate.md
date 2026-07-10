Implement the following circuit:
![Pasted image 20260710194300 1](Pasted%20image%2020260710194300%201.png)

```
module top_module (
    input clk,
    input in, 
    output out);

    wire d;
    assign d = in ^ out;
    
    always @(posedge clk) begin
        out <= d;
    end
    
endmodule

```