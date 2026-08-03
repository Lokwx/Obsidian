Minterm
In an n-variable function, there are 2$^n$ different min terms
> for example A,B,C there are 2$^3$ = 8 combinations of min terms e.g. ABC, $!$ABC

$$
	\text{Given that } \neg ABC \text{ is only true when A = 0, B = 0, C = 1.} 
$$
When $\neg ABC$ is 111, we know that $\neg ABC$ will give 0 because  $0 \cdot 1 \cdot 1 = 0$
> Any wrong input makes at least one factor equal to 0, so the *entire* AND expression becomes 0

$\therefore$ There exists one and *only one* input value such that given minterm = 1, where minterm is the SOP for example $\neg ABC / A\neg BC$

---
Maxterm

| Minterm                                                                                                                                                                            | Maxterm                                                                                                                                                             |     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| Uses AND $\cap$                                                                                                                                                                    | Uses OR $\lor$                                                                                                                                                      |     |
| Equals 1 for one unique input because<br><br>For example<br>$$<br>	A \cap B \cap C<br>$$<br>The only time where it equals to 1 is equal to 1 is <br>$$<br>	A = B = C = 1<br>$$<br> | Equals 0 for one unique input<br><br>For example,<br><br>$$<br>A \lor B \lor C<br>$$<br><br>The only time it equals **0** is when<br><br>$$<br>A = B = C = 0.<br>$$ |     |
| The other scenarios because of $\cap$ the value will be equal to 0 because any other values of $ABC$ will result in the SOP to be 0                                                | The other scenarios because of $\lor$ the value will equal to 1 which is not unique                                                                                 |     |
| There exists only one input such that given maxterm equals to 1                                                                                                                    | There exists only one input such that maxterm equal to 0                                                                                                            |     |

