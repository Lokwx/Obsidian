Implement the circuit described by the Karnaugh map below.

![Pasted image 20260710121505](Pasted%20image%2020260710121505.png)

(!ab!c!d) || (a!b!c!d) || (!a!b!cd) || (ab!cd) || (!abcd) || (a!bcd) || (!a!bc!d) || (abc!d)

```
module top_module(
    input a,
    input b,
    input c,
    input d,
    output out  ); 

    assign out = (!a&&b&&!c&&!d) || (a&&!b&&!c&&!d) || (!a&&!b&&!c&&d) || (a&&b&&!c&&d) || (!a&&b&&c&&d) || (a&&!b&&c&&d) || (!a&&!b&&c&&!d) || (a&&b&&c&&!d);
    
endmodule
```

