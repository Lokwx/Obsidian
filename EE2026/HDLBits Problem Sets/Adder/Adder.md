# Exams/m2014 q4j
Implement the following circuit:

![[Pasted image 20260709212226.png]]

```
module top_module (
    input [3:0] x,
    input [3:0] y, 
    output [4:0] sum);

    wire [4:0] carry;
    assign carry[0] = 0;
    assign sum[4] = carry[4];
    
    genvar i;
    generate
        for (i = 0; i < 4; ++i) begin : loop
            fadd(x[i],y[i],carry[i],carry[i+1],sum[i]);
        end
    endgenerate
    
endmodule

module fadd(input a, input b, input cin, output cout, output sum);
    assign {cout,sum} = a + b + cin;
endmodule

```

### Pointers
Cannot assign different values to the same wire
- Now **two different pieces of hardware are driving the same wire**, which is illegal (or results in multiple drivers and `x` values in simulation).
