For hardware synthesis, there are two types of always blocks that are relevant:

- Combinational: always @(*)
- Clocked: always @(posedge clk)

Clocked always blocks create a blob of combinational logic just like combinational always blocks, but also creates a set of flip-flops (or "registers") at the output of the blob of combinational logic. Instead of the outputs of the blob of logic being visible immediately, the outputs are visible only immediately after the next (posedge clk).

## Blocking vs. Non-Blocking Assignment

There are three types of assignments in Verilog:

- **Continuous** assignments (assign x = y;). Can only be used when **not** inside a procedure ("always block").
- Procedural **blocking** assignment: (x = y;). Can only be used inside a procedure.
- Procedural **non-blocking** assignment: (x <= y;). Can only be used inside a procedure.

### **In a combinational always block, use blocking assignments.** Combinational: always @(*)
### **In a clocked always block, use non-blocking assignments.** Clocked: always @(posedge clk)

A full understanding of why is not particularly useful for hardware design and requires a good understanding of how Verilog simulators keep track of events. Not following this rule results in extremely hard to find errors that are both non-deterministic and differ between simulation and synthesized hardware.

![Pasted image 20260708213636](Pasted%20image%2020260708213636.png)

## Edges
### posedge (Positive edge)
**Definition:** Detects a transition from **0 to 1** (or 0 to X, or X to 1).
**Syntax:** `always @(posedge clk)`

negedge (negative edge)
**Definition:** Detects a transition from **1 to 0** (or 1 to X, or X to 0).
**Syntax:** `always @(negedge clk)`

---

### A bit of practice

Build an XOR gate three ways, using an assign statement, a combinational always block, and a clocked always block. Note that the clocked always block produces a different circuit from the other two: There is a flip-flop so the output is delayed.

```
// synthesis verilog_input_version verilog_2001
module top_module(
    input clk,
    input a,
    input b,
    output wire out_assign,
    output reg out_always_comb,
    output reg out_always_ff   );


	//Continuous Assignment
    assign out_assign = a ^ b;
    
    //Blocking Assignment 
    always @(*) begin out_always_comb = a ^ b; end
    
    //Non-Blocking Assignment
    always @(posedge clk) begin out_always_ff <= a ^ b; end
    
endmodule
```

### Pointers
1. Always be sure of what type of assignment or blocking if you are using
2. If you need the data to update at the end of the clock cycle, then use non-blocking assignment, if not then use blocking assignment/continuous assignment.