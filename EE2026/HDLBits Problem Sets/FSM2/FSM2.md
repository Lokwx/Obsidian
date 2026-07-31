This is a Moore state machine with two states, two inputs, and one output. Implement this state machine.

This exercise is the same as [fsm2s](https://hdlbits.01xz.net/wiki/fsm2s "fsm2s"), but using asynchronous reset.

[![](https://hdlbits.01xz.net/mw/images/b/b8/Fsmjk.png)](https://hdlbits.01xz.net/wiki/File:Fsmjk.png)

```
module top_module(
    input clk,
    input areset,    // Asynchronous reset to OFF
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
    
    always @(posedge clk or posedge areset) begin
        if (areset) state <= OFF;
        else state <= next_state;
    end
    
    assign out = (state == ON);
endmodule

```

### Check the State first, then just code the different states