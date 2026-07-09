Taken from 2015 midterm question 4

See [mt2015_q4a](https://hdlbits.01xz.net/wiki/Mt2015_q4a "Mt2015 q4a") and [mt2015_q4b](https://hdlbits.01xz.net/wiki/Mt2015_q4b "Mt2015 q4b") for the submodules used here. The top-level design consists of two instantiations each of subcircuits A and B, as shown below.![Pasted image 20260709183628](Pasted%20image%2020260709183628.png)

```
Module A: z = (x^y) & x.
Module B: z = !(x ^ y)
```

```
module top_module (input x, input y, output z);
    wire z1,z2,z3,z4,zz1,zz2;
    A A1(x,y,z1);
    B B1(x,y,z2);
    assign zz1 = z1 || z2;
    A A2(x,y,z3);
    B B2(x,y,z4);
    assign zz2 = z3 && z4;
    assign z = zz1 ^ zz2;
    
endmodule

module A (input x, input y, output z);
    assign z = (x^y) & x;
endmodule

module B (input x, input y, output z);
    assign z = !(x ^ y);
endmodule
```