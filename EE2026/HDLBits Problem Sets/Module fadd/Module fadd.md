In this exercise, you will create a circuit with two levels of hierarchy. Your `top_module` will instantiate two copies of `add16` (provided), each of which will instantiate 16 copies of `add1` (which you must write). Thus, you must write _two_ modules: `top_module` and `add1`.

Like [module_add](https://hdlbits.01xz.net/wiki/module_add "module_add"), you are given a module `add16` that performs a 16-bit addition. You must instantiate two of them to create a 32-bit adder. One `add16` module computes the lower 16 bits of the addition result, while the second `add16` module computes the upper 16 bits of the result. Your 32-bit adder does not need to handle carry-in (assume 0) or carry-out (ignored).

Connect the `add16` modules together as shown in the diagram below. The provided module `add16` has the following declaration:

`module add16 ( input[15:0] **a**, input[15:0] **b**, input **cin**, output[15:0] **sum**, output **cout** );`

Within each `add16`, 16 full adders (module `add1`, not provided) are instantiated to actually perform the addition. You must write the full adder module that has the following declaration:

```
module add1 ( input a, input b, input cin, output sum, output cout );
```

![Pasted image 20260708200732](Pasted%20image%2020260708200732.png)

---
### Solution

```
module top_module (
    input [31:0] a,
    input [31:0] b,
    output [31:0] sum
);//
    wire [15:0] s1,s2;
    wire c1,c2;
    add16 i1 (a[15:0], b[15:0], 1'b0, s1, c1);
    add16 i2 (a[31:16], b[31:16], c1, s2, c2);
    assign sum = {s2, s1};
    
endmodule

module add1 ( input a, input b, input cin, output sum, output cout );
	
// Full adder module here
    assign {cout, sum} = a + b + cin;
endmodule
```

### Pointers
1. Always remember that carry is always single bit
	- For example if a + b + cin and it is 3 bits + 3 bits, the result is always a 4 bit number, so take the carry which is the MSB
	- 5 (101) + 5 (101) → 10 (1010), sum = 010, carry = 1
	