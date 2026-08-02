An adder-subtractor can be built from an adder by optionally negating one of the inputs, which is equivalent to inverting the input then adding 1. The net result is a circuit that can do two operations: (a + b + 0) and (a + ~b + 1). See [Wikipedia](https://en.wikipedia.org/wiki/Adder%E2%80%93subtractor) if you want a more detailed explanation of how this circuit works.

Build the adder-subtractor below.

`module add16 ( input[15:0] **a**, input[15:0] **b**, input **cin**, output[15:0] **sum**, output **cout** );`

Use a 32-bit wide XOR gate to invert the b input whenever sub is 1. (This can also be viewed as b[31:0] XORed with sub replicated 32 times. See [replication operator](https://hdlbits.01xz.net/wiki/vector4 "vector4").). Also connect the sub input to the carry-in of the adder.

![Pasted image 20260708212825](Pasted%20image%2020260708212825.png)

---
### Solution

```
module top_module(
    input [31:0] a,
    input [31:0] b,
    input sub,
    output [31:0] sum
);
    wire c1,c2;
    wire [15:0] s1,s2, newb1, newb2;
    	
    assign {newb2, newb1} = {b ^ {32{sub}}};
    
    add16 i1(a[15:0], newb1, sub, s1, c1);
    add16 i2(a[31:16], newb2, c1, s2, c2);
    
    assign sum = {s2,s1};
endmodule
```

### Pointers
1. When doing XOR, it is always bit-wise XOR → So just check if you need to use the replicator in Verilog to ensure that the bits are aligned