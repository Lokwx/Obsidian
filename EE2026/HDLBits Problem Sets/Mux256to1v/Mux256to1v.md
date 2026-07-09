Create a 4-bit wide, 256-to-1 multiplexer. The 256 4-bit inputs are all packed into a single 1024-bit input vector. sel=0 should select bits in[3:0], sel=1 selects bits in[7:4], sel=2 selects bits in[11:8], etc.

```
module top_module( 
    input [1023:0] in,
    input [7:0] sel,
    output [3:0] out );
	
    assign out = in[sel*4 +: 4];
endmodule

```

- Bit slicing ("Indexed vector part select", since Verilog-2001) has an even more compact syntax.

#bitslicing

**specifically for bit slicing (part-selecting)**

`+:` → start at a bit and select **upwards** (towards larger bit numbers).
`-:` → start at a bit and select **downwards** (towards smaller bit numbers).

The syntax is:

```
vector[start -: width]
```

which means:

> Start at `start`, then take `width` bits going downward.

## `+:` (count upwards)

Syntax:

```
data[start +: width]
```

Example:

```
data[8 +: 4]
```

Start at **8**, then go **up** 4 bits.

```
31                                           0
|-------------------------------------------|
             ↑
             8

Take:

11 10 9 8
```

Equivalent to

```
data[11:8]
```

---

Another example:

```
data[16 +: 8]
```

```
Start at 16

Take:

23 22 21 20 19 18 17 16
```

Equivalent to

```
data[23:16]
```

---

# `-:` (count downwards)

Syntax:

```
data[start -: width]
```

Example:

```
data[15 -: 4]
```

Start at **15**, then go **down** 4 bits.

```
31                                           0
|-------------------------------------------|
                    ↑
                   15

Take:

15 14 13 12
```

Equivalent to

```
data[15:12]
```