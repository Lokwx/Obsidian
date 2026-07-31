This is a Moore state machine with two states, two inputs, and one output. Implement this state machine.

This exercise is the same as [fsm2](https://hdlbits.01xz.net/wiki/fsm2 "fsm2"), but using synchronous reset.

[![](https://hdlbits.01xz.net/mw/images/5/5d/Fsmjks.png)](https://hdlbits.01xz.net/wiki/File:Fsmjks.png)

```
module top_module(
    input clk,
    input reset,    // Synchronous reset to OFF
    input j,
    input k,
    output out); //  

    parameter OFF=0, ON=1; 
    reg state, next_state;

    always @(*) begin
        case (state) 
            OFF: 
                if (j) next_state = ON;
            	else next_state = OFF;
            ON:
                if (k) next_state = OFF;
            	else next_state = ON;
        endcase
    end
    
    always @(posedge clk) begin
        if (reset) state <= OFF;
        else state <= next_state;
    end
    
    always @(*) begin
        case (state)
            OFF: out = OFF;
            ON: out = ON;
        endcase
    end

endmodule

```