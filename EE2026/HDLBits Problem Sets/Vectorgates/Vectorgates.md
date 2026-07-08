![697](Pasted%20image%2020260708170816.png)

! → Logical Not
~ → Bitwise Not
### Solution

```
module top_module( 
    input [2:0] a,
    input [2:0] b,
    output [2:0] out_or_bitwise,
    output out_or_logical,
    output [5:0] out_not
);
    assign out_or_bitwise = (a | b);
    assign out_or_logical = a || b;
    assign out_not = {~b[2:0], ~a[2:0]};
    
endmodule
```

