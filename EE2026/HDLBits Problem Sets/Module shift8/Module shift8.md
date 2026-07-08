This exercise is an extension of [module_shift](https://hdlbits.01xz.net/wiki/module_shift "module_shift"). Instead of module ports being only single pins, we now have modules with vectors as ports, to which you will attach wire vectors instead of plain wires. Like everywhere else in Verilog, the vector length of the port does not have to match the wire connecting to it, but this will cause zero-padding or truncation of the vector. This exercise does not use connections with mismatched vector lengths.

You are given a module `my_dff8` with two inputs and one output (that implements a set of 8 D flip-flops). Instantiate three of them, then chain them together to make a 8-bit wide shift register of length 3. In addition, create a 4-to-1 multiplexer (not provided) that chooses what to output depending on `sel[1:0]`: The value at the input d, after the first, after the second, or after the third D flip-flop. (Essentially, `sel` selects how many cycles to delay the input, from zero to three clock cycles.)

The module provided to you is: `module my_dff8 ( input clk, input [7:0] d, output [7:0] q );`

The multiplexer is not provided. One possible way to write one is inside an `always` block with a `case` statement inside. (See also: [mux9to1v](https://hdlbits.01xz.net/wiki/mux9to1v "mux9to1v"))

![Pasted image 20260708180229](Pasted%20image%2020260708180229.png)

```
module my_dff8 ( input clk, input [7:0] d, output [7:0] q );
```

## Reg #reg
To use `if-else` conditions in Verilog, you must place them inside an `always` block. Because `if-else` statements create procedural logic, you must declare the target signal as a reg

### Combinational `if-else` #if-else
 
Use `always @(*)` to create standard combinational logic (e.g., multiplexers or encoders). The `*` automatically senses all signals used in the block.

```
reg out;

always @(*) begin
    if (a == 1'b1) begin
        out = b;
    end else begin
        out = c;
    end
end
```

### Solution

```
module top_module ( 
    input clk, 
    input [7:0] d, 
    input [1:0] sel, 
    output reg [7:0] q 
);
    wire [7:0] q1,q2,q3;
    my_dff8 i1(clk,d,q1);
    my_dff8 i2(clk,q1,q2);
    my_dff8 i3(clk,q2,q3);
    
    always @(*) 
        begin
            if (sel == 2'b00) q = d;
            else if (sel == 2'b01) q = q1;
            else if (sel == 2'b10) q = q2;
            else if (sel == 2'b11) q = q3;
        end
endmodule
```

### Pointers
1. Assign cannot be used in always
2. always @(\*) determines the sensitivity list, it reacts to any input change. If its like posedge clk or posedge reset, then it changes to clock edges
3. = → Blocking (It executes sequentially, the first line finishes before the second line starts)
4. <= → Non-Blocking (Happens at the end of the clock cycle)