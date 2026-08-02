You are given a module `add16` that performs a 16-bit addition. Instantiate two of them to create a 32-bit adder. One add16 module computes the lower 16 bits of the addition result, while the second add16 module computes the upper 16 bits of the result, after receiving the carry-out from the first adder. Your 32-bit adder does not need to handle carry-in (assume 0) or carry-out (ignored), but the internal modules need to in order to function correctly. (In other words, the `add16` module performs 16-bit a + b + cin, while your module performs 32-bit a + b).

Connect the modules together as shown in the diagram below. The provided module `add16` has the following declaration:

```
module add16 ( input[15:0] **a**, input[15:0] **b**, input **cin**, output[15:0] **sum**, output **cout** );
```

![Pasted image 20260708181656](Pasted%20image%2020260708181656.png)

---
### Solution

```
module top_module(
    input [31:0] a,
    input [31:0] b,
    output [31:0] sum
);
    wire [15:0] s1,s2;
    wire cout1,cout2;
    add16 i1(a[15:0], b[15:0], 1'b0, s1, cout1);
    add16 i2(a[31:16], b[31:16], cout1, s2, cout2);
    assign sum = {s2,s1};
endmodule
```
### Pointers
1. When using wires, check if the width is aligned to the input
2. When concatenating, check which one comes first
