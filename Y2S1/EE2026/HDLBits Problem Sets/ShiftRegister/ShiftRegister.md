A **shift register** is a digital circuit that stores binary data (0s and 1s) and **moves (shifts) the data one position left or right every time it receives a clock pulse**.

Think of it like a row of buckets passing balls down the line:

```
Clock Pulse 1:
Input → [1] [0] [1] [1]

Clock Pulse 2:
Input → [X] [1] [0] [1]

Clock Pulse 3:
Input → [X] [X] [1] [0]
```

Each clock pulse shifts every bit one position.

### How it works

A shift register is made from several **flip-flops** connected in series. Each flip-flop stores one bit.

For a 4-bit shift register:

```
Serial Input
     │
     ▼
+----+    +----+    +----+    +----+
|FF1 |--->|FF2 |--->|FF3 |--->|FF4 |
+----+    +----+    +----+    +----+
     ▲
   Clock (shared)
```

On each clock edge:

- FF1 receives the new input bit.
- FF2 gets the previous value of FF1.
- FF3 gets the previous value of FF2.
- FF4 gets the previous value of FF3.

```
module top_module(
    input clk,
    input areset,  // async active-high reset to zero
    input load,
    input ena,
    input [3:0] data,
    output reg [3:0] q); 

    always @(posedge clk or posedge areset) begin 
        if (areset) q <= 0;
        else if (load) q <= data;
        else if (ena)
            q <= {1'b0,q[3:1]};
    end
   
endmodule
```

Use concat to fix the shifting