![Pasted image 20260709180521](Pasted%20image%2020260709180521.png)

```
module top_module (
    input in1,
    input in2,
    output out);
    assign out = !(in1 || in2);
endmodule
```