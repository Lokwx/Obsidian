For each bit in an 8-bit vector, detect when the input signal changes from one clock cycle to the next (detect any edge). The output bit should be set the cycle after a 0 to 1 transition occurs.

Here are some examples. For clarity, in[1] and anyedge[1] are shown separately

![Pasted image 20260711101946](Pasted%20image%2020260711101946.png)

```
module top_module (
    input clk,
    input [7:0] in,
    output reg [7:0] anyedge
);
    reg [7:0] bfrIn = 0;
    always @(posedge clk) begin
        bfrIn <= in;
        anyedge <= (in & ~bfrIn) | (bfrIn & ~in);
    end
endmodule
```

### Pointers
1. Handle the 0 → 1 case by checking what happens when u ~ the bits
	```
in	1100     ~(1100)                                1100
pr	0011       0011                               ~(0011)
	---- -->  ------                         ---> -------
               0011 (wrong as the bit is 0 now)    1100 (correct)
	```
2.  Check if its valid for the other side (1 → 0)
```
in	0011     ~(0011)                 0011
pr	1100       1100                ~(1100)
	---- -->  ------         ---> -------
               1100 (correct)        0011 (wrong)
```
3. Check if the bitwise OR is correct (just test a few)
```
1100     0101
0011     0101
---- --> ----
1111     0101
```