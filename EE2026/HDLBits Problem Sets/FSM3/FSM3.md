The following is the state transition table for a Moore state machine with one input, one output, and four states. Implement this state machine. Include an asynchronous reset that resets the FSM to state A.

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
    input areset,
    output out); //

    parameter A = 0, B = 1, C = 2, D = 3;
    reg [2:0] state,next_state;
    
    always @(*) begin
        case (state)
            A: 
                if (in) next_state = B;
            	else next_state = A;
            B: 
                if (in) next_state = B;
            	else next_state = C;
            C: 
                if (in) next_state = D;
            	else next_state = A;
            D:
                if (in) next_state = B;
            	else next_state = C;
        endcase
    end
   
    always @(posedge clk or posedge areset) begin
        if (areset) state <= A;
        else state <= next_state;
    end
    
    assign out = (state == D);

endmodule
```

### Be aware of the vector length of the states
