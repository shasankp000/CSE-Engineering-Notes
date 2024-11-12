---
title: Compiler Design Practice Problems -- Numericals Only
tags:
  - Semester-5
---
---
# Index

1. [[#1. `First()` and `Follow()` methods recap]]
2. [[#LL(1) compatibility checking]]
3. [[#LL(1) parsing table creation]]
4. [[#Checking if a grammar is SLR(1) compatible.]]
5. [[#Checking whether a grammar is LALR(1) compatible or not]]

---
# 1. `First()` and `Follow()` methods recap

## 1. First() method

### Recapping the rules

1. `First(terminal variable) = terminal variable`
2. `First(ε) = ε` 
3. `Placing ε in any non-terminal variable will completely rule it out and move to the next non-terminal variable(if any)`.
4. `In case of a non-terminal on the RHS, we find the first of that non-terminal, i.e the first of any non-terminal variable will always contain a terminal variable`.

---
#### Example 1

```mathematica
S -> A B c 
A -> a | b A 
B -> d B | ε
```

So the `first(S)` would be `A`.
`first(A) = ab` 
`first(B) = dε`

So we can say that `first(S)` becomes `ab`.

---
#### Example 2

```mathematica
S -> ABC
A -> a | b | ε
B -> c | d | ε
C -> e | f | ε
```
So here we have `first(S) = A`

`first(A) = abε`
`first(B) = cdε`
`first(C) = efε`

So we can also say that `first(S) = abε`

Now as soon as `ε` is placed, `A` will get ruled out and the next non-terminal is considered, which is `B` in this case.

So `first(S) = abcdε`.

Again, in the same way, `B` is ruled out and now `C` is considered.

So `first(S) = abcdefε`. No more non-terminals left to consider so this is the `First()` set of `S`.

---
#### Example 3

```mathematica
E -> TE'
E' -> *TE'|ε
T -> FT'
T' -> ε | +FT'
F -> id|(ε
```

`first(E) = T`
`first(T) = F`
`first(F) = id(`

Thus `first(E) = id(`

---
## 2. Follow() method

### Recapping the rules

1. `Follow(S) where S is the start symbol = {$}`
2. `Follow(A) where A is a non-terminal symbol, goes to it's immediate right.`
3. `In case of a non-terminal variable on the right, we find it's First()`
4. `In case of ε being present on the right of a non-terminal, it's Follow() will be the Follow(LHS), mostly the Follow(S) where S is the start symbol or {$} or any other non-terminal variable on the LHS.`
5. `ε is never included in the Follow set.`
6. `As previously mentioned, applying ε in a non-terminal symbol will rule it out and the next non-terminal symbol will be considered (if any).`

#### Example 1

```mathematica
S -> A B c 
	A -> a | b A 
B -> d B | ε
```

we can re-write the grammar as 

```mathematica
S -> A B c ε
A -> a ε | b A ε 
B -> d B ε | ε
```

So `follow(S)` will include `$`

And  `follow(A) = first(B)`
`first(B) = dε`

Also from `A -> a ε | b A ε `, we see that `ε` maps back to it's start symbol, which is also `A`.

So follow of it's start symbol will be `$`

Therefore `follow(A) = {$, d}`

`ε` was skipped as it is not included in follow sets.

Therefore `follow(B) = c` and from `B -> d B ε | ε`,  there is `ε` on the RHS of B so it maps back to the start symbol, which is also `B`. Now follow of any start symbol is `$`.

So `follow(B) = {$, c}`

---
#### Example 2

```mathematica
S -> A C B
A -> a A | ε
B -> b B | ε
C -> c C | d
```

This grammar can be re-written as :

```mathematica
S -> A C B ε
A -> a A ε | ε
B -> b B ε | ε
C -> c C ε | d ε
```

`follow(S) = {$}`
`follow(A) = {$, first(C)} = {$, cd}`

![[Pasted image 20241110214345.png]]

![[Pasted image 20241110214838.png]]


`follow(B) = {$}`
`follow(C) = {$, first(B)} = {$, b}`, `ε` not included

---
# LL(1) compatibility checking

The LL(1) parser belongs to the category of **Top-Down parsing**.

## LL(1) parsing table creation

1. Find `first()` and `follow()` of all variables
2. Assign numbers to the productions
3. Create the parsing table.
4. Fill in the values based on the `first()` of each variable on RHS  of each production
5. In case of `ε` on the RHS, we will find the `follow()` of the production's start symbol

---
### Example 1

So let's say we have been given a grammar

```mathematica
S -> (L) | a
L -> SL'
L' -> ε | ,SL'
```
This grammar can be re-written as:

```mathematica
S -> (L)ε | aε
L -> SLε'
L' -> ε | ,SL'ε
```
---
#### First sets

`first(S) = {(, a}`
`first(L) = {first(S)} = {(, a}`
`first(L') = {ε, ,}`

---
#### Follow sets


![[Pasted image 20241110223450.png]]


![[Pasted image 20241110224239.png]]


`follow(S) = {$, first(L')} = {$, )}`
`follow(L) = {)}`
`follow(L') = follow(L) = )

---
Now we assign numbers to the productions :

`S -> (L)` = `1`
`S -> a` = `2`
`L -> SL'` = `3`
`L' -> ε` = `4`
`L' -> ,SL'` = `5`

Now we create the parse table ==with each column header containing a terminal symbol ==.
==$ is always present as an extra terminal in the table==
We **CANNOT** use `ε` as a column header in the parse table.

We need to fill the empty part of the table with the numbered productions

| Variables | (   | )   | a   | ,   | $   |
| --------- | --- | --- | --- | --- | --- |
| S         |     |     |     |     |     |
| L         |     |     |     |     |     |
| L'        |     |     |     |     |     |

So we take production 1

`S -> (L)` and we find the `first()` of it's RHS, which is just `(`

So we fill `1` under the `(` symbol.

| Variables | (   | )   | a   | ,   | $   |
| --------- | --- | --- | --- | --- | --- |
| S         | `1` |     |     |     |     |
| L         |     |     |     |     |     |
| L'        |     |     |     |     |     |

As for production 2, `S -> a`, we just write `2` under `a` symbol in the table.

| Variables | (   | )   | a   | ,   | $   |
| --------- | --- | --- | --- | --- | --- |
| S         | `1` |     | `2` |     |     |
| L         |     |     |     |     |     |
| L'        |     |     |     |     |     |

For production 3 `L -> SL'`, `first(L)` = `S`, so we find first of `S` which is `{(, a}`

So we write `3` under the `(` symbol and the `a` symbol

| Variables | (   | )   | a   | ,   | $   |
| --------- | --- | --- | --- | --- | --- |
| S         | `1` |     | `2` |     |     |
| L         | `3` |     | `3` |     |     |
| L'        |     |     |     |     |     |

For production 4, `L' -> ε` , we see that we have `ε` on the RHS. So we find the `follow(L')` which is `{)}`

So we write `4` under the `)` symbol.

| Variables | (   | )   | a   | ,   | $   |
| --------- | --- | --- | --- | --- | --- |
| S         | `1` |     | `2` |     |     |
| L         | `3` |     | `3` |     |     |
| L'        |     | `4` |     |     |     |

And lastly for production 5, `L' -> ,SL'`, the `first(L') = {,}`

So we write `5` under the `,` symbol.

| Variables | (   | )   | a   | ,   | $   |
| --------- | --- | --- | --- | --- | --- |
| S         | `1` |     | `2` |     |     |
| L         | `3` |     | `3` |     |     |
| L'        |     | `4` |     | `5` |     |

Now **if any cell within the LL(1) parse table has more than one entry in it, then the given grammar is NOT LL(1) compatible**.

Here we see that the populated cells have only one entry each.

So, the given grammar, 

```mathematica
S -> (L) | a
L -> SL'
L' -> ε | ,SL'
```

is LL(1) compatible.

---
### Example 2

```mathematica
S -> aSbS | bSaS | ε
```
So we can re-write this grammar as :

```mathematica
S -> aSbSε | bSaSε | ε
```

We need to check whether this grammar is LL(1) compatible or not.

#### First sets

`first(S) = abε`

#### Follow sets

![[Pasted image 20241111120457.png]]

`follow(S) = {$, a, b}`

Therefore the LL(1) parsing table will be:

| Variables | a   | b   | $   |
| --------- | --- | --- | --- |
| S         |     |     |     |

Now we number the productions :

`S -> aSbS`  = `1`.
`S -> bSaS` = `2`.
`S -> ε` = `3`.

Starting with production `1`, we find the `first(S)` which is `a`.

So we write `1` under the column of `a` symbol.

| Variables | a   | b   | $   |
| --------- | --- | --- | --- |
| S         | `1` |     |     |

For production `2`, `first(S) = b`.

So we write `2` under the `b` symbol.

| Variables | a   | b   | $   |
| --------- | --- | --- | --- |
| S         | `1` | `2` |     |

For production `3`, we see that `first(S) = ε`. So it will result in a `follow(S)` which is `{$, a, b}`.
So we will write `3` in all the cells of the table.

Existing values will assume a fractional form as follows: 

| Variables | a     | b     | $   |
| --------- | ----- | ----- | --- |
| S         | `1/3` | `2/3` | `3` |

So here we see that two cells contain more than one value.

So the grammar :

```mathematica
S -> aSbS | bSaS | ε
```

is NOT, LL(1) compatible.

---
# Checking if a grammar is SLR(1) compatible.

**SLR(1) parsing belongs to the parsing type of Bottom-up parsing where the entire production is scanned first by the parser to the bottom then reduced back to it's start symbol at the top**.

Let's say we have been given an example grammar:

```mathematica
E -> T + E | T
T -> id
```

1. We number the productions as we did previously.

`E -> T + E` = `1`.
`E -> T` = `2`.
`T -> id` = `3`.

2. We then, **augment** the grammar by adding a new production rule which points to the start symbol.

`E' -> E`

So the new augmented grammar becomes:

```mathematica
E' -> E
E -> T + E
E -> T
T -> id
```

3. Build the LR(0) canonical item sets.
4. Build the LR(0) Action and Go-To tables
5. Build the SLR(1) Action Table from the LR(0) Action Table
6. If there are no conflicts (shift-reduce or reduce-reduce), then the grammar is SLR(1) compatible

---
## Recapping the concepts of LR(0) canonical items, shifting and reduction LR(0) parsing.

The parsing process happens with the help of **certain items** called canonical items. In this instance, these are called LR(0) canonical items **as SLR(1) parsing depends on LR(0) canonical items**.

So here the parser (atleast in theory let's assume we have a machine called a parser), will **scan** through all the symbols one at a time.

We visually represent this process by using a dot `.`

So, there will be a **stage** when the dot is before a variable (meaning it's not scanned), and a stage after the variable, where it's scanned( which means that production is ready to be reduced.)



So we get these :

- **Production:** `E' -> E`
    
    - Items:

```mathematica
E' -> .E   // Initial item for the start symbol
E' -> E.   // The dot is after the entire production, meaning it's ready for reduction
```
- **Production:** `E -> T + E`

	- Items:

```mathematica
E -> .T + E   // Before anything is parsed
E -> T . + E  // After parsing `T`
E -> T + .E   // After parsing `T +`
E -> T + E.   // After parsing `T + E`
```

- **Production:** `E -> T`
	- Items:

```mathematica
E -> .T      // Before `T` is parsed
E -> T.      // After `T` is parsed (ready for reduction)
```
- **Production:** `T -> id`
	- Items:

```mathematica
T -> .id     // Before `id` is parsed
T -> id.     // After `id` is parsed (ready for reduction)
```

So, the LR(0) items (without closure) are:

```mathematica
E' -> .E
E' -> E.
E -> .T + E
E -> T . + E
E -> T + .E
E -> T + E.
E -> .T
E -> T.
T -> .id
T -> id.
```

Now these items are called **LR(0) canonical items without closure**. 

---
### What is closure by the way?

It's basically the expansion of non-terminal variables, revealing all possible productions like a traversal, and adding unexplored non-terminals to the right of the dot, to consider them as **parsed**.

Like opening a folder to see their contents inside.

It only works on **non-terminal variables**.

---

So after applying closure, the items will be **grouped into sets**, called **canonical item sets**.

So here we have the first production:

`E' -> .E`

![[Pasted image 20241111132622.png]]

So here to form a closure of `E'`, it needs to be expanded.

![[Pasted image 20241111124028.png]]

So accommodating all expansions of `E'`, we get the first LR(0) canonical item set $I_0$ as :

```mathematica
E' → .E
E → .T + E
E → .T
T → .id
```
Now to open the folder of `E` or expand on `E`, the parser needs to **shift over** `E` first so that it's ready for reduction.

So we get a new LR(0) canonical item set $I_1$ as :

```mathematica
E' -> E.
```

![[Pasted image 20241111132728.png]]


Next we open the folder of `E` or expand on `E` (however you say it).

![[Pasted image 20241111124710.png]]

So we get to see the two productions which `E` leads to and the parser shifts over the first variable, `T` in both cases, meaning the variable `T` is ready for reduction.

So we get a new LR(0) canonical item set $I_2$ as:

```mathematica
E → T. + E
E → T.
```

![[Pasted image 20241111132857.png]]


Now we can't parse the next variable **as it's a terminal variable** and closure only works on **non-terminal variables**, but the parser can **still shift beyond the terminal to access any remaining non-terminals**.

So the parser just shifts over the terminal symbol `+` to get a new production 

`E -> T + .E`

So, we get a new canonical item set $I_3$ as :

```mathematica
E -> T +. E
E → .T + E
E → .T
T → .id
```

**Why are not the remaining productions shifted over too?**

```mathematica
E → .T + E
E → .T
T → .id
```
These?

Because :
1. `T` has already been parsed over, so we don't need to shift the dots again over the remaining `T`.
   
   In:
   
   ```mathematica
	E → T. + E
	E → T.
	```
   `T` has already been **shifted over**.
   
   So we **don't expand T again**.
   
   And in :
   
   ```mathematica
   E' -> E.
	```
   `E` has already been parsed completely.
   
   So even after shifting over to get :
   
   ```mathematica
   E → T + E.
	```
   We **don't expand E again**. 
   
2. ==The way the shifting is done is dictated by the rules of the original grammar==. These "canonical item sets" we see are **in-between phases** of parsing, so we don't follow their "rules" to shift over again.

![[Pasted image 20241111133010.png]]

So from $I_3$, after shifting the dot over `E` we get a new LR(0) canonical item $I_4$ as :

```mathematica
E → T + E.
```
![[Pasted image 20241111133103.png]]

And shifting the dot over terminal `id` we get the last LR(0) canonical item $I_5$ set as :

```mathematica
T -> id.
```

And thus finally all non-terminals have been expanded and are ready for reduction.

---
### What Exactly is **Reduction** in LR Parsing?

**Reduction** in LR parsing means that the parser has matched a sequence of input symbols that corresponds to the **right-hand side (RHS)** of a production rule, and it now replaces this sequence with the **left-hand side (LHS)** of the production.

Reduction is the reverse of derivation:

- In **derivation**, you expand non-terminals into terminals using production rules.
- In **reduction**, you collapse terminals back into non-terminals using the production rules.

It’s like a `substitution method`, but only works if it’s possible to substitute the entire `input/production` rule back to the **original numbered production**.

Reduction **only works**, if the entire **production rule / terminal** has been parsed, and **end of input has been reached.** The parser then checks whether it’s possible to reduce the **entire rule / terminal**, back to the **augmented start symbol**.

This is how **reduction** works in bottom-up parsing, where it gradually builds back up to the start symbol.

---
### What exactly is Shifting in LR parsing?

#### **Shifts (`S`)**:

- **Shift** means to “read” a symbol from the input and move to a new state.
- `S3` means **Shift** the input symbol (i.e., read it) and then move to state `3`.

The number after `S` refers to the **state** the parser should transition to after the shift. Here’s how it works:

- The current state looks at the next input symbol (let’s say it’s `+`).
- If the table entry says `S3`, it means “Shift the input symbol `+`, consume it, and go to state `3`”.

For example, if you’re in **state 0** and the next input symbol is `id`, the Action table might say `S5`. This means the parser will shift (consume `id`) and move to **state 5**.

---
## Creating the LR(0) Action and Go-To Tables

Recapping our LR(0) canonical items

- **I₀:**

```mathematica
E' → .E
E → .T + E
E → .T
T → .id
```

- **I₁:**

```mathematica
E' -> E.
```

- **I₂:**

```mathematica
E -> T. + E
E -> T.
```

- **I₃:**

```mathematica
E → T + .E
E → .T + E
E → .T
T → .id
```

- **I₄:** from (I3​), `E -> T + .E`

```mathematica
E -> T + E.
```

- I5​: (from I0​)

```mathematica
T -> id.
```

And our **numbered productions**

We number these productions as 1, 2 and 3

`E -> T + E` = 1 
`E -> T` = 2 
`T -> id` = 3

---
### Creating the LR(0) Action Table.

![[Pasted image 20241111144153.png]]

All the state transitions are depicted in this picture.

**The action table denotes transitions over terminal symbols and the reductions**

We create the action table as follows :

The column headers are all the terminal symbols because that's where the shifting takes place.

| States | `id` | `+` | `$` |
| ------ | ---- | --- | --- |
| $I_0$​ |      |     |     |
| $I_1$​ |      |     |     |
| $I_2$​ |      |     |     |
| $I_3$​ |      |     |     |
| $I_4$​ |      |     |     |
| $I_5$​ |      |     |     |

For terminal `id` we see that $I_0$ goes to $I_5$ from the image.

So $I_0$ will shift over `id` to $I_5$

So we write `S5` to represent “Shift to State 5”.

| States | `id` | `+` | `$` |
| ------ | ---- | --- | --- |
| $I_0$​ | `S5` |     |     |
| $I_1$​ |      |     |     |
| $I_2$​ |      |     |     |
| $I_3$​ |      |     |     |
| $I_4$​ |      |     |     |
| $I_5$​ |      |     |     |

The augmented grammar has `E'` as the new start symbol, and the goal of the parser is to reduce everything down to `E' → E`.

In $I_1$​ we see that `E' -> E.`, the input has been reduced to the start symbol `E'`, and the dot at the end means that the entire derivation of the grammar has been successfully parsed.

So $I_1$​ is the **accept** state.

| States | `id` | `+` | `$`        |
| ------ | ---- | --- | ---------- |
| $I_0$​ | `S5` |     |            |
| $I_1$​ |      |     | **accept** |
| $I_2$​ |      |     |            |
| $I_3$​ |      |     |            |
| $I_4$​ |      |     |            |
| $I_5$​ |      |     |            |

The reason the **accept** word is written under `$` symbol is because there is no shift/reduction happening here.

For $I_2$ we see that it shifts over to $I_3$ for `+` terminal.

So we write `S3` denoting "Shift to State 3"

The parser sees that `E -> T.` is present in $I_2$​ which can be completely reduced back to **numbered production 2**.

So we write `R2`, to represent **Reduction to rule 2**, in all the columns of that row.

| States | `id` | `+`     | `$`        |
| ------ | ---- | ------- | ---------- |
| $I_0$​ | `S5` |         |            |
| $I_1$​ |      |         | **accept** |
| $I_2$​ | `R2` | `S3/R2` | `R2`       |
| $I_3$​ |      |         |            |
| $I_4$​ |      |         |            |
| $I_5$​ |      |         |            |

Now dealing with $I_3$ , we see that it shifts over `id` to $I_5$.

So we write `S5` to represent “Shift to State 5”.

| States | `id` | `+`     | `$`        |
| ------ | ---- | ------- | ---------- |
| $I_0$​ | `S5` |         |            |
| $I_1$​ |      |         | **accept** |
| $I_2$​ | `R2` | `S3/R2` | `R2`       |
| $I_3$​ | `S5` |         |            |
| $I_4$​ |      |         |            |
| $I_5$​ |      |         |            |

Now for $I_4$, `E -> T + E.` can be completely reduced back to production `1`. So we write `R1` in the entire row, denoting `Reduce to rule 1`.

| States | `id` | `+`     | `$`        |
| ------ | ---- | ------- | ---------- |
| $I_0$​ | `S5` |         |            |
| $I_1$​ |      |         | **accept** |
| $I_2$​ | `R2` | `S3/R2` | `R2`       |
| $I_3$​ | `S5` |         |            |
| $I_4$​ | `R1` | `R1`    | `R1`       |
| $I_5$​ |      |         |            |

And for $I_5$, `T -> id.`, can be completely reduced back to production `3`. So we write `R3` in the entire row, denoting `Reduce to rule 3`.

| States | `id` | `+`     | `$`        |
| ------ | ---- | ------- | ---------- |
| $I_0$​ | `S5` |         |            |
| $I_1$​ |      |         | **accept** |
| $I_2$​ | `R2` | `S3/R2` | `R2`       |
| $I_3$​ | `S5` |         |            |
| $I_4$​ | `R1` | `R1`    | `R1`       |
| $I_5$​ | `R3` | `R3`    | `R3`       |

This is the **LR(0) Action Table**, ==which is necessary to understand before creating== the **SLR(0) Action Table**.

---
### Creating the LR(0) Go-To table

Referencing the image again :

![[Pasted image 20241111144153.png]]


The Go-To table denotes **shifts over all non-terminal variables**.

The non-terminal shifts here are only for 

$I_0$ to $I_1$ for `E`  --> `S1`
$I_0$ to $I_2$ for `T` --> `S2`
$I_3$ to $I_4$ for `E` --> `S4`
$I_3$ to $I_2$ for `T` --> `S2`

So this is our initial **Go-To** table.

| State  | E   | T   |
| ------ | --- | --- |
| $I_0$​ |     |     |
| $I_1​$ |     |     |
| $I_2$​ |     |     |
| $I_3$​ |     |     |
| $I_4$​ |     |     |
| $I_5$​ |     |     |

And after filling in all the transitions, we get :

| State  | E    | T    |
| ------ | ---- | ---- |
| $I_0$​ | `S1` | `S2` |
| $I_1​$ |      |      |
| $I_2$​ |      |      |
| $I_3$​ | `S4` | `S2` |
| $I_4$​ |      |      |
| $I_5$​ |      |      |

Here is our final LR(0) Go-to Table.

---

The actual LR(0) **parsing table** is the combination of both of these tables.

|States|`id`|`+`|`$`|E|T|
|---|---|---|---|---|---|
|I0​|`S5`|||I1​|I2​|
|I1​|||accept|||
|I2​|`R2`|`S3`/`R2`|`R2`|||
|I3​|`S5`|||I4​|I2​|
|I4​|`R1`|`R1`|`R1`|||
|I5​|`R3`|`R3`|`R3`|||

---
## Creating the SLR(1) parsing table.

The SLR(1) Go-To table is the same as the LR(0) Go-To table, however there is a significant difference between the Action Tables of the two.

As we can see in the LR(0) parsing table, one cell has both a shift and a reduction at the same time.

**This is called a shift-reduce conflict, which  SLR(1) and LR(0) DO NOT allow**.

So to make the action table for SLR(1) we need to see if the removal of the shift-reduce conflict and the reduce-reduce conflict is possible or not. If yes, then the given grammar will be compatible with an SLR(1) parser.

So, we start with the current LR(0) Action Table

| States | `id` | `+`     | `$`        |
| ------ | ---- | ------- | ---------- |
| $I_0$​ | `S5` |         |            |
| $I_1$​ |      |         | **accept** |
| $I_2$​ | `R2` | `S3/R2` | `R2`       |
| $I_3$​ | `S5` |         |            |
| $I_4$​ | `R1` | `R1`    | `R1`       |
| $I_5$​ | `R3` | `R3`    | `R3`       |

$I_2$ has a reduction to rule 2, and a shift reduce conflict as well.

So we need to find the follow of the LHS of this rule here.
![[Pasted image 20241111145839.png]]


So we write `R2` under $\$$ symbol

| States | `id` | `+`  | `$`        |
| ------ | ---- | ---- | ---------- |
| $I_0$​ | `S5` |      |            |
| $I_1$​ |      |      | **accept** |
| $I_2$​ |      | `S3` | `R2`       |
| $I_3$​ | `S5` |      |            |
| $I_4$​ | `R1` | `R1` | `R1`       |
| $I_5$​ | `R3` | `R3` | `R3`       |

For $I_4$ :

![[Pasted image 20241111145924.png]]

So we write `R1` under $\$$ symbol

| States | `id` | `+`  | `$`        |
| ------ | ---- | ---- | ---------- |
| $I_0$​ | `S5` |      |            |
| $I_1$​ |      |      | **accept** |
| $I_2$​ |      | `S3` | `R2`       |
| $I_3$​ | `S5` |      |            |
| $I_4$​ |      |      | `R1`       |
| $I_5$​ | `R3` | `R3` | `R3`       |

And for $I_5$ :

![[Pasted image 20241111150508.png]]

Therefore we will place `R3` under both `+` and $\$$ symbols

| States | `id` | `+`  | `$`        |
| ------ | ---- | ---- | ---------- |
| $I_0$​ | `S5` |      |            |
| $I_1$​ |      |      | **accept** |
| $I_2$​ |      | `S3` | `R2`       |
| $I_3$​ | `S5` |      |            |
| $I_4$​ |      |      | `R1`       |
| $I_5$​ |      | `R3` | `R3`       |

Now we see that **there are no-more shift-reduce conflicts**, so this grammar is **SLR(1) compatible**, but **LR(0) incompatible**.

This means that **SLR(1) may accept extra grammars which are not LR(0) compatible**.

---
# Checking whether a grammar is LALR(1) compatible or not

LALR(1) parser is another type of Top-Down parser which is based on LR(1) parser.

The LR(1) parser works on LR(1) grammar which is slightly different than it's LR(0) counterpart.

The process to generate the LR(1) canonical items is similar to the LR(0) process, except that we need to track a **lookahead symbol**.

1. Construct LR(1) canonical items
2. Construct LR(1) Action and Go-To table
3. See if merging of states is possible or not, without any conflicts.
4. If possible, then the grammar is LALR(1) compatible, else it is not LALR(1) compatible.

---

So let's say we have an example grammar here: 

```mathematica
S -> aAd | bBd | aBe | bAe
A -> c
B -> c
```
We proceed similarly, first augmenting the grammar and numbering the original productions.

```mathematica
S' -> S
S -> aAd | bBd | aBe | bAe
A -> c
B -> c
```

`S->aAd` = 1 
`S-> bBd` = 2 
`S -> aBe` = 3
`S -> bAe` = 4 
`A -> c` = 5
`B -> c` = 6

---
## Step 2. Construct the first unclosured LR(1) item

$I_0$:

```mathematica
S' -> .S    , [$]
S  -> .aAd  , [$]
S  -> .bBd  , [$]
S  -> .aBe  , [$]
S  -> .bAe  , [$]
A -> .c, [$]
B -> .c, [$]
```

where the dot indicates that it hasn’t parsed anything yet, and each production of S is followed by the lookahead symbol `$`.

We get a new canonical item $I_1$ as

```mathematica
S' -> S.    , [$]
```

which is the accepting state as the original start symbol has been parsed.

---
## Step 3. Construct Go-To operations on terminal symbols first.

For `a` ,

We can get a new canonical item $I_2$

```mathematica
S  -> a.Ad  , [$]
S  -> a.Be  , [$]
```

Now we see that the dot is in front of non-terminals `A` and `B`, so they need to expanded further.

```mathematica
A -> .c, [$]
B -> .c, [$]
```
However in this instance the lookahead for `c` won't be `$`, since there are terminals `d` and `e` after the expansion of the non-terminals `A` and `B`. So we the new lookahead symbols will be `d` and `e` respectively

```mathematica
A -> .c, [d]
B -> .c, [e]
```

So the final $I_2$ becomes :
```mathematica
S  -> a.Ad  , [$]
S  -> a.Be  , [$]
A -> .c, [d]
B -> .c, [e]
```

In a similar way, we can find the next canonical item $I_3$ for terminal `b`.

```mathematica
S  -> b.Bd  , [$]
S  -> b.Ae  , [$]
A -> .c, [e]
B -> .c, [d]
```
---
## Step 4. Perform Go-To operations on non-terminals.

Right now, the parser is at a stage where it needs to shift and parse over the non-terminal symbols before parsing the remaining terminal symbols.

So from items $I_1$ and $I_2$, we get:

$I_4$​:

```mathematica
S -> aA.d  , [$]
```

$I_5$:

```mathematica
S -> aB.e  , [$]
```

$I_6$:

```mathematica
S -> bA.e, [$]
```

$I_7$​:

```mathematica
S -> bB.d, [$]
```
---
## Step 5. Perform Go-To operations on remaining terminal symbols

Now that the non-terminal symbols have been parsed, we can parse the remaining terminal symbols

There are still a few remaining terminals, `c`, `d` and `e`.

For `d` and `e`

And from states $I_4$, and $I_5$,  we get:

`S  -> aAd.  ,[$]`  -> $I_8$
`S  -> aBe.  , [$]` -> $I_9$

And from states $I_6$ and $I_7$, we get: 

`S  -> bBd.  , [$]` -> $I_{10}$
`S  -> bAe.  , [$]` -> $I_{11}$


And for `c`:

We see that from $I_2$: `A -> .c, [d]` and `B -> .c, [e]` can have the dot shifted over to get

 $I_{12}$:
```mathematica
A -> c. , [d]
B ->c. , [e]
```

And from $I_3$ : `A -> .c, [e]`  and `B -> .c, [d]` can have the dot shifted over to get

$I_{13}$:
```mathematica
A -> c. , [e]  
B ->c. , [d]
```

So, the final recollection of all **LR(1)** canonical items

![[Pasted image 20241112131153.png]]

---
## Step 6. Building the LR(1) and Go-To tables

The **Action table** deals with shifts, reduces, and accepts. We look at the items with:

- Shift actions: When there is a dot before a terminal symbol.
- Reduce actions: When a production is completed (dot at the end of a rule).
- Accept action: When we have `S' -> S. , [$]` in some item set.


We construct our empty **LR(1)** action table

| States   | a   | b   | c   | d   | e   | $   |
| -------- | --- | --- | --- | --- | --- | --- |
| $I_0$    |     |     |     |     |     |     |
| $I_1$    |     |     |     |     |     |     |
| $I_2$    |     |     |     |     |     |     |
| $I_3$    |     |     |     |     |     |     |
| $I_4$    |     |     |     |     |     |     |
| $I_5$    |     |     |     |     |     |     |
| $I_6$    |     |     |     |     |     |     |
| $I_7$    |     |     |     |     |     |     |
| $I_8$    |     |     |     |     |     |     |
| $I_9$    |     |     |     |     |     |     |
| $I_{10}$ |     |     |     |     |     |     |
| $I_{11}$ |     |     |     |     |     |     |
| $I_{12}$ |     |     |     |     |     |     |
| $I_{13}$ |     |     |     |     |     |     |

Referencing our image again,

![[Pasted image 20241112131156.png]]

We see that for terminal `a`, $I_0$ goes to state $I_2$ 
For terminal `b`, $I_0$ goes to state $I_3$

And $I_1$ is the accepting state here.

Therefore we denote those shifts with `S2` and `S3`

| States   | a    | b    | c   | d   | e   | $          |
| -------- | ---- | ---- | --- | --- | --- | ---------- |
| $I_0$    | `S2` | `S3` |     |     |     |            |
| $I_1$    |      |      |     |     |     | **accept** |
| $I_2$    |      |      |     |     |     |            |
| $I_3$    |      |      |     |     |     |            |
| $I_4$    |      |      |     |     |     |            |
| $I_5$    |      |      |     |     |     |            |
| $I_6$    |      |      |     |     |     |            |
| $I_7$    |      |      |     |     |     |            |
| $I_8$    |      |      |     |     |     |            |
| $I_9$    |      |      |     |     |     |            |
| $I_{10}$ |      |      |     |     |     |            |
| $I_{11}$ |      |      |     |     |     |            |
| $I_{12}$ |      |      |     |     |     |            |
| $I_{13}$ |      |      |     |     |     |            |

For terminal `c`, $I_2$ goes to $I_{12}$ and $I_3$ goes to $I_{13}$

So, we denote those shifts using `S12` and `S13`

| States   | a    | b    | c     | d   | e   | $          |
| -------- | ---- | ---- | ----- | --- | --- | ---------- |
| $I_0$    | `S2` | `S3` |       |     |     |            |
| $I_1$    |      |      |       |     |     | **accept** |
| $I_2$    |      |      | `S12` |     |     |            |
| $I_3$    |      |      | `S13` |     |     |            |
| $I_4$    |      |      |       |     |     |            |
| $I_5$    |      |      |       |     |     |            |
| $I_6$    |      |      |       |     |     |            |
| $I_7$    |      |      |       |     |     |            |
| $I_8$    |      |      |       |     |     |            |
| $I_9$    |      |      |       |     |     |            |
| $I_{10}$ |      |      |       |     |     |            |
| $I_{11}$ |      |      |       |     |     |            |
| $I_{12}$ |      |      |       |     |     |            |
| $I_{13}$ |      |      |       |     |     |            |

For terminal `d`, $I_4$ and $I_5$ go to $I_8$ and $I_9$ each.

So we denote the shifts using `S8` and `S9`.

| States   | a    | b    | c     | d    | e   | $          |
| -------- | ---- | ---- | ----- | ---- | --- | ---------- |
| $I_0$    | `S2` | `S3` |       |      |     |            |
| $I_1$    |      |      |       |      |     | **accept** |
| $I_2$    |      |      | `S12` |      |     |            |
| $I_3$    |      |      | `S13` |      |     |            |
| $I_4$    |      |      |       | `S8` |     |            |
| $I_5$    |      |      |       | `S9` |     |            |
| $I_6$    |      |      |       |      |     |            |
| $I_7$    |      |      |       |      |     |            |
| $I_8$    |      |      |       |      |     |            |
| $I_9$    |      |      |       |      |     |            |
| $I_{10}$ |      |      |       |      |     |            |
| $I_{11}$ |      |      |       |      |     |            |
| $I_{12}$ |      |      |       |      |     |            |
| $I_{13}$ |      |      |       |      |     |            |

For terminal `e`, $I_6$ and  $I_7$ go to $I_{10}$ and $I_{11}$ each.

So we denote those shifts using `S10` and `S11`.

| States   | a    | b    | c     | d    | e     | $          |
| -------- | ---- | ---- | ----- | ---- | ----- | ---------- |
| $I_0$    | `S2` | `S3` |       |      |       |            |
| $I_1$    |      |      |       |      |       | **accept** |
| $I_2$    |      |      | `S12` |      |       |            |
| $I_3$    |      |      | `S13` |      |       |            |
| $I_4$    |      |      |       | `S8` |       |            |
| $I_5$    |      |      |       | `S9` |       |            |
| $I_6$    |      |      |       |      | `S10` |            |
| $I_7$    |      |      |       |      | `S11` |            |
| $I_8$    |      |      |       |      |       |            |
| $I_9$    |      |      |       |      |       |            |
| $I_{10}$ |      |      |       |      |       |            |
| $I_{11}$ |      |      |       |      |       |            |
| $I_{12}$ |      |      |       |      |       |            |
| $I_{13}$ |      |      |       |      |       |            |

![[Pasted image 20241112131156.png]]


Now from the image, we see that, states $I_8$ to $I_{13}$ are all reducible states.

Recapping our original numbered productions:

`S->aAd` = 1
`S-> bBd` = 2
`S -> aBe` = 3
`S -> bAe` = 4
`A -> c` = 5
`B -> c` = 6


So the reduction goes like this,

$I_8$  has `S  -> aAd.  ,[$]` which can be reduced back to rule `1`
$I_9$ has `S  -> aBe.  , [$]`, which can be reduced back to rule `3`
$I_{10}$ has `S  -> bBd.  , [$]`, which can be reduced back to rule `2`
$I_{11}$ has `S  -> bAe.  , [$]`, which can be reduced back to rule `4`

$I_{12}$ has :
```mathematica
A -> c., [d]
B -> c., [e]
```
which reduce to rules `5` and `6` 

and $I_{13}$ has: 

```mathematica
A -> c., [e]
B -> c., [d]
```
which, again reduce to rule `5` and `6`.

So the resulting Action Table accordingly will be:

| States   | a    | b    | c     | d    | e     | $          |
| -------- | ---- | ---- | ----- | ---- | ----- | ---------- |
| $I_0$    | `S2` | `S3` |       |      |       |            |
| $I_1$    |      |      |       |      |       | **accept** |
| $I_2$    |      |      | `S12` |      |       |            |
| $I_3$    |      |      | `S13` |      |       |            |
| $I_4$    |      |      |       | `S8` |       |            |
| $I_5$    |      |      |       | `S9` |       |            |
| $I_6$    |      |      |       |      | `S10` |            |
| $I_7$    |      |      |       |      | `S11` |            |
| $I_8$    |      |      |       |      |       | `R1`       |
| $I_9$    |      |      |       |      |       | `R3`       |
| $I_{10}$ |      |      |       |      |       | `R2`       |
| $I_{11}$ |      |      |       |      |       | `R4`       |
| $I_{12}$ |      |      |       | `R5` | `R6`  |            |
| $I_{13}$ |      |      |       | `R6` | `R5`  |            |

---
### Constructing the LR(1) Go-To table

As usual, the Go-To table will focus on transitions over non-terminal symbols

We have non-terminals **A** and **B**.


![[Pasted image 20241112131156.png]]

Referencing our image again, we see that :

$I_0$ goes to $I_1$ for non-terminal `S`.

$I_2$ goes to $I_4$ for non-terminal `A`.
$I_2$ goes to $I_5$ for non-terminal `B`.

$I_3$ goes to $I_6$ for non-terminal `B`.
$I_3$ goes to $I_7$ for non-terminal `A`.

So the final LR(1) parsing table will be :

| States   | a    | b    | c     | d    | e     | $          | S    | A    | B    |
| -------- | ---- | ---- | ----- | ---- | ----- | ---------- | ---- | ---- | ---- |
| $I_0$    | `S2` | `S3` |       |      |       |            | `S1` |      |      |
| $I_1$    |      |      |       |      |       | **accept** |      |      |      |
| $I_2$    |      |      | `S12` |      |       |            |      | `S4` | `S5` |
| $I_3$    |      |      | `S13` |      |       |            |      | `S7` | `S6` |
| $I_4$    |      |      |       | `S8` |       |            |      |      |      |
| $I_5$    |      |      |       | `S9` |       |            |      |      |      |
| $I_6$    |      |      |       |      | `S10` |            |      |      |      |
| $I_7$    |      |      |       |      | `S11` |            |      |      |      |
| $I_8$    |      |      |       |      |       | `R1`       |      |      |      |
| $I_9$    |      |      |       |      |       | `R3`       |      |      |      |
| $I_{10}$ |      |      |       |      |       | `R2`       |      |      |      |
| $I_{11}$ |      |      |       |      |       | `R4`       |      |      |      |
| $I_{12}$ |      |      |       | `R5` | `R6`  |            |      |      |      |
| $I_{13}$ |      |      |       | `R6` | `R5`  |            |      |      |      |

---
## Step 7. Checking if merging of states is possible or not.

**LALR parser works by merging similar states into a single state, thus reducing the number of shifts.**

Here we see that we have two similar states under different lookaheads `d` and `e`

![[Pasted image 20241112140052.png]]

and 

![[Pasted image 20241112140107.png]]

Both can be merged into a single state, **however this will lead to a reduce-reduce conflict which LALR(1) parser DOES NOT allow**.

---
### How does the reduce-reduce conflict arise?

Well, since these two states had initially separate reductions under the different lookaheads

| $I_{12}$ |      |      |       | `R5` | `R6`  |
| -------- | ---- | ---- | ----- | ---- | ----- |
| $I_{13}$ |      |      |       | `R6` | `R5`  |

On being merged :

![[Pasted image 20241112142949.png]]

The reductions will be in a single cell now, which will cause a reduce-reduce conflict.

Thus this grammar is **NOT LALR(1) compatible**.

However, for an example grammar which is indeed compatible, check example 2 from this video :

https://www.youtube.com/watch?v=GOlsYofJjyQ&list=PLxCzCOWd7aiEKtKSIHYusizkESC42diyc&index=15

---
