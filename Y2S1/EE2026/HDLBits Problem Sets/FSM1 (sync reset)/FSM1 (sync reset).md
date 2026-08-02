This is a Moore state machine with two states, one input, and one output. Implement this state machine. Notice that the reset state is B.

This exercise is the same as [fsm1](https://hdlbits.01xz.net/wiki/fsm1 "fsm1"), but using synchronous reset.

[![](https://hdlbits.01xz.net/mw/images/8/82/Fsm1s.png)](https://hdlbits.01xz.net/wiki/File:Fsm1s.png)


```
// Note the Verilog-1995 module declaration syntax here:
module top_module(clk, reset, in, out);
    input clk;
    input reset;    // Synchronous reset to state B
    input in;
    output out;//  
    reg out;

    // Fill in state name declarations
    parameter A=0,B=1;
    reg present_state, next_state;
    
    always @(*) begin
        case (in) 
            1'b0: next_state = (present_state == A ? B : A);
            default: next_state = present_state;
        endcase
    end
    
    always @(posedge clk) begin
        if (reset) present_state <= B;
        else present_state <= next_state;
    end
    
    always @(*) begin 
        case (present_state)
            A: out = A;
            B: out = B;
        endcase
    end

endmodule

```

an FSM really has **three jobs**:

1. decide the next state (combinational block) → Changes when any values inside the sensitivity list changes
2. store the state on the clock edge → Only changes at the clock edge
3. generate the output from the state (combinational block) → Changes when any values inside the sensitivity list changes