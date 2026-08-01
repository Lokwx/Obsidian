See also: [State transition logic for this FSM](https://hdlbits.01xz.net/wiki/Fsm3comb "Fsm3comb")

The following is the state transition table for a Moore state machine with one input, one output, and four states. Implement this state machine. Include a synchronous reset that resets the FSM to state A. (This is the same problem as [Fsm3](https://hdlbits.01xz.net/wiki/Fsm3 "Fsm3") but with a synchronous reset.)

|State|Next state|   |Output|
|---|---|---|---|
|in=0|in=1|
|A|A|B|0|
|B|C|B|0|
|C|A|D|0|
|D|C|B|1|

```
module top_module(
    input clk,
    input in,
    input reset,
    output out); //

	parameter A=0,B=1,C=2,D=3;
    reg [1:0] state,next_state;
    
    always @(*) begin 
        case (state)
            A: next_state = in ? B : A;
            B: next_state = in ? B : C;
            C: next_state = in ? D : A;
            D: next_state = in ? B : C;
        endcase
    end
    
    always @(posedge clk) begin
        if (reset) state <= A;
   		else state <= next_state;
    end
    
    always @(*) begin out = (state == D); end

endmodule
```



