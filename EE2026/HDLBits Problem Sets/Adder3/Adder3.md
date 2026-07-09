Now that you know how to build a [full adder](https://hdlbits.01xz.net/wiki/Fadd "Fadd"), make 3 instances of it to create a 3-bit binary ripple-carry adder. (You need to write the full adder module as part of the submitted code, possibly by reusing your solution to [fadd](https://hdlbits.01xz.net/wiki/fadd "fadd").)

The adder adds two 3-bit numbers and a carry-in to produce a 3-bit sum and carry out. To encourage you to actually instantiate full adders, also output the carry-out from _each_ full adder in the ripple-carry adder. cout[2] is the final carry-out from the last full adder, and is the carry-out you usually see.

```
module top_module( 
    input [2:0] a, b,
    input cin,
    output [2:0] cout,
    output [2:0] sum );

    wire [3:0] carry;
    assign carry[0] = cin;
    assign cout = carry[3:1];
    
    genvar i;
    generate
        for (i = 0; i < 3; ++i) begin : loop
            fadd m1(a[i],b[i],carry[i],carry[i+1],sum[i]);
        end
    endgenerate
    
endmodule

module fadd(input a, input b, input cin, output cout, output sum);
    assign {cout,sum} = a + b + cin;
endmodule
```

