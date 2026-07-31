
This is a Moore state machine with two states, one input, and one output. Implement this state machine. Notice that the reset state is B.

This exercise is the same as [fsm1s](https://hdlbits.01xz.net/wiki/fsm1s "fsm1s"), but using asynchronous reset.

[![](https://hdlbits.01xz.net/mw/images/7/70/Fsm1.png)](https://hdlbits.01xz.net/wiki/File:Fsm1.png)

```
module top_module(
    input clk,
    input areset,    // Asynchronous reset to state B
    input in,
    output out);//  

    parameter A=0, B=1; 
    reg state, next_state;

    always @(*) begin    // This is a combinational always block
        // State transition logic
        case (in) 
            1'b0: next_state = (state == A ? B : A);
            1'b1: next_state = state;
        endcase
    end

    always @(posedge clk, posedge areset) begin    // This is a sequential always block
        // State flip-flops with asynchronous reset
        if (areset) state <= B;
        else state <= next_state;
    end

    // Output logic
    // assign out = (state == ...);

            assign out = (state == B);     
endmodule

```