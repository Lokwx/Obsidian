_This is the second component in a series of five exercises that builds a complex counter out of several smaller circuits. See [the final exercise](https://hdlbits.01xz.net/wiki/exams/review2015_fancytimer "exams/review2015_fancytimer") for the overall design._

Build a finite-state machine that searches for the sequence 1101 in an input bit stream. When the sequence is found, it should set start_shifting to 1, forever, until reset. Getting stuck in the final state is intended to model going to other states in a bigger FSM that is not yet implemented. We will be extending this FSM in the next few exercises
![[Pasted image 20260801213545.png]]

```
module top_module (
    input clk,
    input reset,      // Synchronous reset
    input data,
    output start_shifting);

    parameter zero = 0,one = 1,two = 2,three = 3, flag = 5;
    reg [2:0] state,next_state;
    
    always @(*) begin
        case (state)
            zero: next_state = data ? one : zero;
            one: next_state = data ? two : zero;
            two: next_state = data ? two : three;
            three: next_state = data ? flag : zero;
		endcase
    end
    
    always @(posedge clk) begin
        if (reset) state <= zero;
        else state <= next_state;
    end
    
    always @(*) begin 
        start_shifting = (state == flag);
    end
    
endmodule

```