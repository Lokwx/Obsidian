Implement the circuit described by the Karnaugh map below.

![Pasted image 20260710121201](Pasted%20image%2020260710121201.png)

d = 1
a || (!b && c)

```
module top_module(
    input a,
    input b,
    input c,
    input d,
    output out  ); 

    assign out = a || (!b && c);
    
endmodule

```