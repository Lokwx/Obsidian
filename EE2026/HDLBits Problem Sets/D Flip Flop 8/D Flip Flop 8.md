Create 8 D flip-flops. All DFFs should be triggered by the positive edge of clk.

```
module top_module (
    input clk,
    input [7:0] d,
    output reg [7:0] q
);

    genvar i;
    generate 
        for (i = 0; i < 8; ++i) begin : loop
            dffs m1(clk,d[i],q[i]);
        end
    endgenerate
endmodule

module dffs(input clk, input d, output reg q); 
    always @(posedge clk) begin
        q <= d;
    end
endmodule
```

### Pointers
1. Blocking vs Non-Blocking assignment for Flip Flops
2. Flip Flops uses non-blocking assignment (Must happen together)
3. Normal Calculation uses blocking assignment

### 1. Blocking Assignment (`=`)

- **Behavior:** Executes sequentially. The statement must finish before the next statement in the block executes.
    
- **Hardware Mapping:** In simulation, it behaves like an immediate update. If you use this in a `posedge` block, you are creating a simulation race condition because the value of `q` will depend on the order of the statements, rather than the state of the circuit at the clock edge.
    
- **Primary Use:** Combinational logic (e.g., `always @(*)`).

### 2. Non-blocking Assignment (`<=`)

- **Behavior:** Schedules the update to occur at the end of the current simulation time step. All `a <= b` statements are evaluated using the values of variables _at the start_ of the clock edge, and the updates are applied simultaneously afterward.
    
- **Hardware Mapping:** Accurately models a D flip-flop, where the output is updated based on the input stable at the clock edge.
    
- **Primary Use:** Sequential logic (e.g., `always @(posedge clk)`).