_This is the third component in a series of five exercises that builds a complex counter out of several smaller circuits. See [the final exercise](https://hdlbits.01xz.net/wiki/exams/review2015_fancytimer "exams/review2015_fancytimer") for the overall design._

As part of the FSM for controlling the shift register, we want the ability to enable the shift register for exactly 4 clock cycles whenever the proper bit pattern is detected. We handle sequence detection in [Exams/review2015_fsmseq](https://hdlbits.01xz.net/wiki/Exams/review2015_fsmseq "Exams/review2015 fsmseq"), so this portion of the FSM only handles enabling the shift register for 4 cycles.

Whenever the FSM is reset, assert shift_ena for 4 cycles, then 0 forever (until reset).

![Pasted image 20260801213611](Pasted%20image%2020260801213611.png)

```
module top_module (
    input clk,
    input reset,      // Synchronous reset
    output shift_ena);

    parameter zero=0,one=1,two=2,three=3,flag=5;
    reg [2:0] state,next_state;
    
    always @(*) begin
        case (state)
            zero: next_state = one;
            one: next_state = two;
            two: next_state = three;
            three: next_state = flag;
        endcase
    end
            
    always @(posedge clk) begin
        if (reset) state <= zero;
        else state <= next_state;
    end
    
    assign shift_ena = ~(state == flag);
    
endmodule

```