You are given a module `my_dff` with two inputs and one output (that implements a D flip-flop). Instantiate three of them, then chain them together to make a shift register of length 3. The `clk` port needs to be connected to all instances.

The module provided to you is: `module my_dff ( input clk, input d, output q );`

Note that to make the internal connections, you will need to declare some wires. Be careful about naming your wires and module instances: the names must be unique.

![Pasted image 20260708175947](Pasted%20image%2020260708175947.png)

---
### Solution

```
### Module Declaration

module my_dff ( input clk, input d, output q );
```

```
module top_module ( input clk, input d, output q );
    wire q1,q2;
    my_dff i1(clk, d, q1);
    my_dff i2(clk, q1, q2);
    my_dff i3(clk, q2, q);
endmodule
```
