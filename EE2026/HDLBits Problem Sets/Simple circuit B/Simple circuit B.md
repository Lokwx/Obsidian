Taken from 2015 midterm question 4

Circuit B can be described by the following simulation waveform:![[Pasted image 20260709183559.png]]

```
module top_module ( input x, input y, output z );
    assign z = !(x ^ y);
endmodule
```