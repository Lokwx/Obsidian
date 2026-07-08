![Pasted image 20260708164702](Pasted%20image%2020260708164702.png)![Pasted image 20260708164710|697](Pasted%20image%2020260708164710.png)
### Solution

```
`default_nettype none
module top_module(
    input a,
    input b,
    input c,
    input d,
    output out,
    output out_n   ); 

    wire w1, w2;
    assign w1 = (a && b);
    assign w2 = (c && d);
    assign out = w1 || w2;
    assign out_n = !(w1 || w2);
    
endmodule
```
