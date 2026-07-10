Consider the function _f_ shown in the Karnaugh map below. Implement this function.

(The original exam question asked for simplified SOP and POS forms of the function.)
![Pasted image 20260710161307](Pasted%20image%2020260710161307.png)

```
module top_module (
    input [4:1] x,
    output f
); 
    assign f = (!x[2] && !x[4]) || (!x[1] && x[3]) || (x[2] && x[3] && x[4]);
endmodule

```