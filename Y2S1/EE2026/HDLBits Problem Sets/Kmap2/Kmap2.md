Implement the circuit described by the Karnaugh map below.

![Pasted image 20260710113746](Pasted%20image%2020260710113746.png)


!a && !d || !b && !c || bcd || acd


```
module top_module(
    input a,
    input b,
    input c,
    input d,
    output out  ); 
	
    assign out = (!a && !d) || (!b && !c) || (b && c && d) || (a && c && d);
    
endmodule

```