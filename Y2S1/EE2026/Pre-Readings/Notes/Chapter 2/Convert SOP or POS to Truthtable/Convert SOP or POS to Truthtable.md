To reverse the process, remember these things
1) Maxterm → POS → Sum (OR) are equal to 0
	> So basically you just paste those OR that give u the combination to be 0 in the truth table, then the rest then u fill in 1
2) Minterm → SOP → Product (AND) that is equal to 1
	> You just paste those AND combinations that is written in the SOP then u just fill in the truth table

**f they are derived from the same Boolean function**, then **canonical SOP and canonical POS will always produce exactly the same truth table**.

The only difference is **how you describe the function**.

---

### Example

Suppose the truth table is:

|A|B|F|
|---|---|---|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|

### SOP (look at the 1's)

$\overline A B + A\overline B$

POS (look at the 0's)

$(A+B)(\overline A + \overline B)$

---

Reversing it:

|A|B|SOP|POS|
|---|---|---|---|
|00|0|0|0|
|01|1|1|1|
|10|1|1|1|
|11|0|0|0|

They are **identical**. Its just how you represent it