#forloops

Given a 100-bit input vector [99:0], reverse its bit ordering.
### Module Declaration

module top_module( 
    input [99:0] in,
    output [99:0] out
);

### For Loop Syntax
```
always_comb begin
   
    // 1. The for loop starts here
    for (int i = 0; i < 4; i++) begin
        // Perform the iterative operation
        if (data[i]) begin
            found = 1'b1;
        end
    end
    // 2. Logic ends
end
```

### Solution

```
module top_module( 
    input [99:0] in,
    output [99:0] out
);
	
    always_comb begin
        for (int i = 99; i >= 0; --i) begin
            out[99-i] = in[i];
        end
    end
    
endmodule
```