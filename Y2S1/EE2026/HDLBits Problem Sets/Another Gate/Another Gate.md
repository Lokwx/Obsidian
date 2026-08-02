![Pasted image 20260709180622](Pasted%20image%2020260709180622.png)

```
module top_module (
    input in1,
    input in2,
    output out);
    assign out = !in2 && in1;
endmodule
```