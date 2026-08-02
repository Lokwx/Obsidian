#Priorityencoder

A _priority encoder_ is a combinational circuit that, when given an input bit vector, outputs the position of the first 1 bit in the vector. For example, a 8-bit priority encoder given the input 8'b10010000 would output 3'd4, because bit[4] is first bit that is high.

Build a 4-bit priority encoder. For this problem, if none of the input bits are high (i.e., input is zero), output zero. Note that a 4-bit number has 16 possible combinations.

---
### Solution

```
// synthesis verilog_input_version verilog_2001
module top_module (
    input [3:0] in,
    output reg [1:0] pos);
	
    always @(*) begin
        if (in[0]) pos = 2'd0;
        else if (in[1]) pos = 2'd1;
        else if (in[2]) pos = 2'd2;
        else if (in[3]) pos = 2'd3;
        else pos = 2'd0;
    end
    
endmodule

```

### Pointers
1. Sequence of the if else statements is very important, if we are checking the first one bit, then we would need to place in[0] at the front instead of in[3] because it checks the largest bit instead of the smallest bit