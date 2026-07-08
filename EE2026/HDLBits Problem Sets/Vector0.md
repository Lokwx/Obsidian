wire **[99:0]** my_vector; // Declare a 100-element vector assign out = my_vector[10]; // Part-select one bit out of the vector

![[Pasted image 20260708160055.png]]

```
module top_module ( 
    input wire [2:0] vec,
    output wire [2:0] outv,
    output wire o2,
    output wire o1,
    output wire o0  ); // Module body starts after module declaration

    assign outv = vec;
    assign o2 = vec[2];
    assign o1 = vec[1];
    assign o0 = vec[0];
    
endmodule
```
