---
{"dg-publish":true,"permalink":"/flat-speedrun/context-free-languages-and-context-free-grammar-the-ultimate-breakdown/","title":"Context Free Languages and Context-Free Grammar -- Formal Language and Automata Theory","tags":["Semester-4"],"created":"2025-03-06T18:33:20.655+05:30","updated":"2025-08-24T23:34:43.440+05:30"}
---


---

# Context Free Language

![Pasted image 20240617085935.png](/img/user/Images/Pasted%20image%2020240617085935.png)

The main difference between CFL and a Regular language is that of the production rule.
In RL the production rule is not an iteration, that is, it cannot contain an empty symbol.

However in a CFL the production rule is a closure, that is it can contain an empty symbol.

## Example

![Pasted image 20240617090110.png](/img/user/Images/Pasted%20image%2020240617090110.png)

![Pasted image 20240617113550.png](/img/user/Images/Pasted%20image%2020240617113550.png)

![Pasted image 20240617114234.png](/img/user/Images/Pasted%20image%2020240617114234.png)

![Pasted image 20240617114254.png](/img/user/Images/Pasted%20image%2020240617114254.png)

![Pasted image 20240617115954.png](/img/user/Images/Pasted%20image%2020240617115954.png)



https://www.youtube.com/watch?v=htoFbcwES28&list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev&index=72

---
# Derivation Tree

https://www.youtube.com/watch?v=u4-rpIlV9NI&list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev&index=73

![Pasted image 20240617120038.png](/img/user/Images/Pasted%20image%2020240617120038.png)

![Pasted image 20240617120210.png](/img/user/Images/Pasted%20image%2020240617120210.png)

---

# Ambiguous Grammar

![Pasted image 20240617120709.png](/img/user/Images/Pasted%20image%2020240617120709.png)

Here instead of drawing a tree, the variables were used on the left and right side respectively.

---

# Simplification of CFG : Basics

https://www.youtube.com/watch?v=EF09zxzpVbk&list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev&index=75

![Pasted image 20240617121321.png](/img/user/Images/Pasted%20image%2020240617121321.png)

![Pasted image 20240617121344.png](/img/user/Images/Pasted%20image%2020240617121344.png)

![Pasted image 20240617121407.png](/img/user/Images/Pasted%20image%2020240617121407.png)

## Example

![Pasted image 20240617121601.png](/img/user/Images/Pasted%20image%2020240617121601.png)

*Phase 1*

STEP 1: Make a *set of all the terminal symbols* (small letters)

$T = \{a,c,e\}$

And a *set of the non-terminal symbols* $W_1$

$W_1 = \{A,C,E\}$ 

Now make another set $W_2$ *which contains all the symbols of $W_1$* and the symbols ==which can derive these symbols==.

We add the symbol *S* in $W_2$ since *S* can derive the symbols *A* and *C*

Therefore, $W_2 = \{A, C ,E, S\}$

Continue this if anymore symbols can be added, or else stop.

---

*Phase 2*

Make a new Grammar *G'* which is an equivalent of grammar *G*, such that :

$G' = \{ (V), (T), P, (S)  \}$

where V = variables/non-terminal symbols, T = terminal symbols, P = production rules and S = Start symbol

Thus the new production rule P will be : S -> AC, A->a, C->c, E->aA | e .

We ==ignored== *B* in this rule since *B was not included in any of the sets*.

Now make a new set $Y_1$ which contain the start symbol *S*

Therefore, $Y_1 = \{S\}$ 

And make another set $Y_2$ which will contain S and all the symbols derivable from S.

$Y_2 = \{S, A, C\}$ 

Now make another set $Y_3$ which will contain all the current symbol as well as all the *terminal symbols* derivable from $Y_2$ .

Thus, $Y_3 = \{ S, A, C, a, c \}$

Notice how E and it's derivations got skipped as well. Since E was redundant.

Thus the new reduced grammar.

![Pasted image 20240617123532.png](/img/user/Images/Pasted%20image%2020240617123532.png)

---
# Simplification of CFG : Removal of Unit productions

https://www.youtube.com/watch?v=B2o75KpzfU4&list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev&index=76

![Pasted image 20240617123727.png](/img/user/Images/Pasted%20image%2020240617123727.png)

## Example ![Pasted image 20240617123802.png](/img/user/Images/Pasted%20image%2020240617123802.png)

Here we need to find the type of productions which are of the type A->B and B->any sort of terminal symbols.

Basically following a whole transitive approach.

So, we can find in the example that :

M -> N and N -> a.

So we can simply *substitute* M->a instead.

P becomes : S->XY, X->a, Y->Z|b, Z->M, M->a

Again the same applies for Z->M, M->a

We can *substitute* Z->a instead.

Therefore, P : S->XY, X->a, Y->Z|b, Z->a

Now again the same applies to Y->Z and Z->a.

We can *substitute* Y->a instead.

Therefore, P : S->XY, X->a, Y->a|b

It may seem that S->X|Y and the same applies here too since X->a, Y->a|b, but we ==don't modify the start symbol==.

Therefore the reduced grammar will be :

P : S->XY, X->a, Y->a|b.

---
# Simplification of CFG (removal of NULL productions)

https://www.youtube.com/watch?v=mlXYQ8ug2v4&list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev&index=77

![Pasted image 20240617124920.png](/img/user/Images/Pasted%20image%2020240617124920.png)

STEP 1: Find all productions in the form of $A -> \in$ 
STEP 2: Replace those productions with just $\in$ 

![Pasted image 20240617125150.png](/img/user/Images/Pasted%20image%2020240617125150.png)

So basically we will pair the original productions with the non-terminal variables on the left, followed by the  |  and the replaced variants of the symbol on the right

Therefore in S, we can get the following production:

S -> ABAC
S -> ABC | BAC | BC

For A->aA | $\in$ 

we get : A -> a

similarly for B -> bB | $\in$ 

B -> b

Therefore the new production accordingly will be :

![Pasted image 20240617130540.png](/img/user/Images/Pasted%20image%2020240617130540.png)

---

# Chomsky Normal Form(CNF) and CFG to GNF conversion

https://www.youtube.com/watch?v=Mh-UQVmAxnw&list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev&index=78

In Chomsky Normal Form, we have a *restriction on the length of RHS*, which is, ==elements in RHS should either be two variables or a Terminal variable==. 

![Pasted image 20240617130836.png](/img/user/Images/Pasted%20image%2020240617130836.png)

where *A*, *B*, *C* are non-terminals and *a* is a terminal variable.

![Pasted image 20240617131044.png](/img/user/Images/Pasted%20image%2020240617131044.png)

## Conversion of CFG to CNF

https://www.youtube.com/watch?v=FNPSlnj3Vt0&list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev&index=79 [Recommended to watch]


## Example 

![Pasted image 20240617172959.png](/img/user/Images/Pasted%20image%2020240617172959.png)

Step 1: Check if there is a start symbol on the right hand side of the production
Step 2: If so, then create a production $S'-> S$ :

![Pasted image 20240617173127.png](/img/user/Images/Pasted%20image%2020240617173127.png)

Step 3: Remove NULL productions

![Pasted image 20240617173238.png](/img/user/Images/Pasted%20image%2020240617173238.png)

Here we first remove $B->\in$ , followed by $A->\in$ 

Step 4: Remove all Unit Productions

![Pasted image 20240617173528.png](/img/user/Images/Pasted%20image%2020240617173528.png)\

![Pasted image 20240617173626.png](/img/user/Images/Pasted%20image%2020240617173626.png)

Here in STEP 4: We found the productions that has more than two variables in RHS.

Thus we have to replace the variables SA with a new one named X.

and in STEP 5: we replaced *a* with the variable Y. 

Both STEP 4 and STEP 5 needed to be enacted since they were violating CNF.

---

# Greibach Normal Form and CFG to GNF conversion

![Pasted image 20240617174025.png](/img/user/Images/Pasted%20image%2020240617174025.png)

![Pasted image 20240617174110.png](/img/user/Images/Pasted%20image%2020240617174110.png)

![Pasted image 20240617174653.png](/img/user/Images/Pasted%20image%2020240617174653.png)

So initially we checked if the given grammar had any unit or null productions [Check Passed]
Next we checked whether the CFG is already in CNF or not. [Check Passed]
So then we simply rename the variables into a form of $A_i$ with the value of i starting from 1.

Now we need to alter the rules such that there are no non-terminal symbols $A_i$ > $A_j$ or 
$A_i -> A_j x$, where i < j .

Here we find in production 2 that $A_4$ > $A_1$ 

Thus we need to fix that as follows :

Thus we replace the value of $A_1$ in production 2.

![Pasted image 20240617180610.png](/img/user/Images/Pasted%20image%2020240617180610.png)

And we see that the same variable is repeating on the RHS.

This is called left recursion.

## Removal of Left recursion

![Pasted image 20240617181727.png](/img/user/Images/Pasted%20image%2020240617181727.png) 

replace the repeating variable with a new variable Z and write with the variable Z once and without it again.

Now write the variable $A_4$ as it is and then with the new variable Z.

![Pasted image 20240617182232.png](/img/user/Images/Pasted%20image%2020240617182232.png)


---
# Pumping Lemma for CFL


![Pasted image 20240617223522.png](/img/user/Images/Pasted%20image%2020240617223522.png)

Same as Pumping lemma for RL, except that the string S needs to be broken down into 5 parts

*u*, *v*, *x*, *y*, and *z* .

![Pasted image 20240617223616.png](/img/user/Images/Pasted%20image%2020240617223616.png)


![Pasted image 20240617223634.png](/img/user/Images/Pasted%20image%2020240617223634.png)

## Example 


![Pasted image 20240617223652.png](/img/user/Images/Pasted%20image%2020240617223652.png)

Let the pumping length P = 4

Therefore we get two cases :

![Pasted image 20240617223811.png](/img/user/Images/Pasted%20image%2020240617223811.png)

![Pasted image 20240617223819.png](/img/user/Images/Pasted%20image%2020240617223819.png)

Here we can see that the number of a, b and c are not the same according to the rule of the language. 

Thus this language is not context-free

One more example video

https://www.youtube.com/watch?v=DPs8sBcIjs8&list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev&index=84

---
# Pushdown Automata

![Pasted image 20240617224304.png](/img/user/Images/Pasted%20image%2020240617224304.png)

![Pasted image 20240617224355.png](/img/user/Images/Pasted%20image%2020240617224355.png)

![Pasted image 20240617224417.png](/img/user/Images/Pasted%20image%2020240617224417.png)

## Formal definition

https://www.youtube.com/watch?v=eY7fwj5jvC4&list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev&index=87

![Pasted image 20240617224728.png](/img/user/Images/Pasted%20image%2020240617224728.png)
$\gamma$ is read as "gamma". 

![Pasted image 20240617224818.png](/img/user/Images/Pasted%20image%2020240617224818.png)

![Pasted image 20240618065916.png](/img/user/Images/Pasted%20image%2020240618065916.png)

![Pasted image 20240618070330.png](/img/user/Images/Pasted%20image%2020240618070330.png)

This one right here is non-deterministic pushdown automata.

---
# Pushdown Automata -- Even Palindromes

![Pasted image 20240618070946.png](/img/user/Images/Pasted%20image%2020240618070946.png)

Here we have designed non-deterministic PDA in which it's a bit hard to figure out, when we have reached the middle of the string.

So we introduce epsilon between every string. https://www.youtube.com/watch?v=BxA-aI2dyRo&list=PLBlnK6fEyqRgp46KUv4ZY69yXmpwKOIev&index=89

![Pasted image 20240618072015.png](/img/user/Images/Pasted%20image%2020240618072015.png)

This results in a huge tree of possible inputs

![Pasted image 20240618072042.png](/img/user/Images/Pasted%20image%2020240618072042.png)
![Pasted image 20240618072105.png](/img/user/Images/Pasted%20image%2020240618072105.png)

