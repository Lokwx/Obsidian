#ProductOfSums
### Max Terms (Product of Sums) → Output is a 1
1. Search for output to 0
2. If !A!B!C  = 0, we will write it as the complement so (ABC)
3. If !A!BC = 0, we will write it as the complement (AB!C)
4. Then we write it as a product of sums

#SumOfProducts
### Min Terms (Sum of Products) → Output is a 1
1. Search for output to 1
2. Then just follow the normal K-Map simplification (no complement is required)


A single-output digital system with four inputs (a,b,c,d) generates a logic-1 when 2, 7, or 15 appears on the inputs, and a logic-0 when 0, 1, 4, 5, 6, 9, 10, 13, or 14 appears. The input conditions for the numbers 3, 8, 11, and 12 never occur in this system. For example, 7 corresponds to a,b,c,d being set to 0,1,1,1, respectively.

Determine the output out_sop in minimum SOP form, and the output out_pos in minimum POS form.

```
module top_module (
    input a,
    input b,
    input c,
    input d,
    output out_sop,
    output out_pos
); 
    assign out_sop = (c && d) || (c && !a && !b);
    assign out_pos = (c) && (d || !a) && (d || !b);
endmodule
```
