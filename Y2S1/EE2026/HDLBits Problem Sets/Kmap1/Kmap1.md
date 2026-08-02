Implement the circuit described by the Karnaugh map below.

![Pasted image 20260710112706](Pasted%20image%2020260710112706.png)

a || c || b



```
module top_module(
    input a,
    input b,
    input c,
    output out  ); 

    assign out = a || c || b;
endmodule

```