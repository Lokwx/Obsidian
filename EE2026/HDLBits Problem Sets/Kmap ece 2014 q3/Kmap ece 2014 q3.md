For the following Karnaugh map, give the circuit implementation using one 4-to-1 multiplexer and as many 2-to-1 multiplexers as required, but using as few as possible. You are not allowed to use any other logic gate and you must use _a_ and _b_ as the multiplexer selector inputs, as shown on the 4-to-1 multiplexer below.

You are implementing just the portion labelled **top_module**, such that the entire circuit (including the 4-to-1 mux) implements the K-map.

![Pasted image 20260710161635](Pasted%20image%2020260710161635.png)

(The requirement to use only 2-to-1 multiplexers exists because the original exam question also wanted to test logic function simplification using K-maps and how to synthesize logic functions using only multiplexers. If you wish to treat this as purely a Verilog exercise, you may ignore this constraint and write the module any way you wish.)

```
module top_module (
    input c,
    input d,
    output [3:0] mux_in
); 
    assign mux_in[2] = !d;
    assign mux_in[1] = 0;
    
    //!a!b case (or)
    always @(*) begin
        case (c)
            1'b1: mux_in[0] = 1'b1;
            1'b0: mux_in[0] = d; 
        endcase
    end
    
    //ab case (and)
    always @(*) begin
        case (c)
            1'b1: mux_in[3] = d;
            1'b0: mux_in[3] = 0; 
        endcase
    end
    
endmodule
```
