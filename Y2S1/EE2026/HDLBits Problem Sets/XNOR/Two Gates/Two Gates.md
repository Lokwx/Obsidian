![Pasted image 20260709180716](Pasted%20image%2020260709180716.png)
```
module top_module (
    input in1,
    input in2,
    input in3,
    output out);
    assign out = in3 ^ !(in1 ^ in2);
endmodule
```