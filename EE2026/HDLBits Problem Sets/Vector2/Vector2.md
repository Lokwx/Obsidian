A 32-bit vector can be viewed as containing 4 bytes (bits [31:24], [23:16], etc.). Build a circuit that will reverse the _byte_ ordering of the 4-byte word.

AaaaaaaaBbbbbbbbCcccccccDddddddd => DdddddddCcccccccBbbbbbbbAaaaaaaa

This operation is often used when the [endianness](https://en.wikipedia.org/wiki/Endianness) of a piece of data needs to be swapped, for example between little-endian x86 systems and the big-endian formats used in many Internet protocols.

```
### Module Declaration

module top_module( 
    input [31:0] in,
    output [31:0] out );
```


## Wrong (Cannot reorder endian when its set) 
### e.g. input [31:0] input cannot be accessed using assign out [7:0] = input[0:7]

```
    assign out[7:0] = in[0:7];
    assign out[15:8] = in[8:15];
    assign out[23:16] = in[16:23];
    assign out[31:24] = in[24:31];
```

### Solution

```
module top_module( 
    input [31:0] in,
    output [31:0] out );//

    // assign out[31:24] = ...;
    assign out = {in[7:0], in[15:8], in[23:16], in[31:24]};
    
endmodule
```

Use concat method ```
assign out = {in[7:0], in[15:8], in[23:16], in[31:24]}; ```
to assign in blocks