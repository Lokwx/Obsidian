#forloops 

Create a 100-bit binary ripple-carry adder by instantiating 100 [full adders](https://hdlbits.01xz.net/wiki/Fadd "Fadd"). (You also need to write the full adder module, possibly by reusing your solution to [fadd](https://hdlbits.01xz.net/wiki/fadd "fadd").)

The adder adds two 100-bit numbers and a carry-in to produce a 100-bit sum and carry out. To encourage you to actually instantiate full adders, also output the carry-out from _each_ full adder in the ripple-carry adder. cout[99] is the final carry-out from the last full adder, and is the carry-out you usually see.

### Solution
```
module top_module( 
    input [99:0] a, b,
    input cin,
    output [99:0] cout,
    output [99:0] sum );

    wire [100:0] carry;
    
    assign carry[0] = cin;
    assign cout = carry[100:1];
    
    genvar i;
    generate
        for (i = 0; i < 100; i++) begin : adder_loop
            fadd m1(a[i],b[i],carry[i],carry[i+1],sum[i]);
        end
    endgenerate
    
endmodule

module fadd(input a, input b, input cin, output cout, output sum);
    assign {cout,sum} = a + b + cin;
endmodule
```

### Pointers
1. Redo this question
