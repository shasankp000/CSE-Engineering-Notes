---
{"dg-publish":true,"permalink":"/compiler-design/module-7-intermediate-code-generation/","title":"Intermediate Code Generation -- Compiler Design","tags":["Semester-5"],"created":"2025-03-06T18:33:20.269+05:30"}
---

---
# Index

1. [[#Intermediate Code Generation]]
2. [[#Intermediate Languages]]
3. [[#1. Three-address code (TAC)]]
4. [[#2. Abstract Syntax Trees (AST)]]
5. [[#3. Directed Acyclic Graphs (DAG)]]
6. [[#4. Postfix evaluation.]]
7. [[#Three-Address Codes in Intermediate Code Generation]]
8. [[#Representation of TAC]]
9. [[#1. Quadruples]]
10. [[#2. Triples]]
11. [[#Problem with Triples and Execution Order]]
12. [[#3. Indirect Triples]]
13. [[#How Indirect Triples Work]]
---
# Intermediate Code Generation

**Intermediate Code Generation** is a crucial phase in the process of compiling a source program into machine code. It acts as a bridge between the source code and the target machine code, making the compiler design more modular and efficient. ==During this phase, the compiler translates the source program into an intermediate representation (IR) that is easier to analyze, manipulate, and optimize before generating the final machine code==.

---

## Purpose of Intermediate Code

1. **Portability**: ==Intermediate code is platform-independent==, meaning the same IR can be used for generating code for different target machines by just changing the back-end code generation.
2. **Optimization**: ==Many code optimizations are easier to perform at the intermediate level than on the source or machine code==.
3. **Simplification**: It simplifies the compiler design by breaking the compilation process into multiple stages.
4. **Error Detection**: Many semantic errors in the source code can be caught at this stage during the semantic analysis and intermediate representation generation.

---

## Characteristics of Intermediate Representations

1. **Simplicity**: Easier to manipulate and analyze than the source language or machine code.
2. **Abstraction**: Provides an abstraction over the hardware, making it suitable for multiple platforms.
3. **Compactness**: Should be compact to allow efficient storage and processing.
4. **Expressiveness**: Must be capable of representing all constructs of the source language efficiently.

---
# Intermediate Languages

https://www.youtube.com/watch?v=j-bLeUysUiE&list=PLxCzCOWd7aiEKtKSIHYusizkESC42diyc&index=24

==Intermediate languages are the formats or structures used to represent intermediate code. They can take several forms depending on the requirements of the compiler==. Let’s explore the types of intermediate languages:


![Pasted image 20241116123853.png](/img/user/media/Pasted%20image%2020241116123853.png)

## 1. Three-address code (TAC):

- ==Represents the program as a sequence of instructions, where each instruction has at most three operands==.
- Each instruction typically involves one operator and three operands: two source operands and one destination.
- Example:
```c
t1 = a + b
t2 = t1 * c
d = t2 - e
```
- Here, `t1`, `t2` are temporary variables used to store intermediate results.

or 

![Pasted image 20241116124554.png](/img/user/media/Pasted%20image%2020241116124554.png)

More on this is continued in [[#Three-Address Codes in Intermediate Code Generation]].

---
## 2. Abstract Syntax Trees (AST):

- A tree representation of the program's structure based on its syntax.
- Example: For the expression `(a + b) * c`, the AST would look like:
  
```mathematica
    *
   / \
  +   c
 / \
a   b

```

Or for the expression `(b*c) + (b*c)`:

![Pasted image 20241116124023.png](/img/user/media/Pasted%20image%2020241116124023.png)

This would be an AST for the expression.

---
## 3. Directed Acyclic Graphs (DAG):

- A condensed form of AST that eliminates redundant computations by sharing sub-expressions.
- Example: If `(a + b)` is computed multiple times in a program, it would appear as a single node in the DAG.

Or for the expression `(b*c) + (b*c)`:

![Pasted image 20241116124140.png](/img/user/media/Pasted%20image%2020241116124140.png)

This image would be an accurate DAG representation for the expression.

---
## 4. Postfix evaluation.

This is similar to the postfix evaluation done in DSA.

![Pasted image 20241116124252.png](/img/user/media/Pasted%20image%2020241116124252.png)


The process of postfix evaluation is detailed here: https://www.geeksforgeeks.org/evaluation-of-postfix-expression/

or a video explanation here : https://www.youtube.com/watch?v=84BsI5VJPq4

---
# Three-Address Codes in Intermediate Code Generation

https://www.youtube.com/watch?v=tJUYVGDn0JE&list=PLxCzCOWd7aiEKtKSIHYusizkESC42diyc&index=23

## Structure of TAC

A typical three-address code instruction is of the form:

```c
x = y op z
```

Where:

- `x`: The destination or result variable.
- `y`, `z`: Source operands (could be variables, constants, or temporary variables).
- `op`: An operator (e.g., arithmetic, logical, or relational).

---
## Advantages of TAC

1. **Modularity**: ==It breaks complex operations into simpler steps, making the program easier to analyze==.
2. **Optimization**: ==TAC provides a clear structure for applying optimization techniques like common subexpression elimination, constant folding, and dead code elimination==.
3. **Simplicity**: Its simplicity makes it easier to generate machine code for different architectures.
4. **Portability**: TAC is platform-independent, allowing the same representation to be used across different backends.
---
## Types of Three-Address Code Instructions:


![Pasted image 20241116125859.png](/img/user/media/Pasted%20image%2020241116125859.png)

Terminologies which might look confusing: 

1. **relop** : "Relational operator"
2. "**op**": "Operator"

![Pasted image 20241116130040.png](/img/user/media/Pasted%20image%2020241116130040.png)

---

1. **Assignment Statements**:
```c
x = y op z
```
Example: `t1 = a + b`

---
2. **Unary Operations**: 
```c
x = op y
```
Example: `t1 = -a` (negation)

---
3. **Copy Instructions**:

```c
x = y
```
Example: `t1 = a`

----
4. **Unconditional Jumps**:   
```c
goto L
```
Example: `goto L1`

---
5. **Conditional Jumps**:
```c
if x relop y goto L
```
Example: `if a > b goto L2`

----
6. **Indexed Assignments**:
```c
x = y[i]
y[i] = x
```
Example: 
```c
t1 = A[i]   // Read from array
A[i] = t2   // Write to array
```
---
7. **Function Calls and Returns**:
```c
param x
call P, n
x = call P, n
return x
```
Example:
```c
param a
call foo, 1
return t1
```
---
## Representation of TAC

Three-address code can be represented in three forms:

https://www.youtube.com/watch?v=O0HCUfGsEK0

---
### 1. Quadruples:
   
   - **Each instruction is represented as a tuple of four fields, each with a final result name.**:

```c
(operator, arg1, arg2, result)
``` 

- Example: For `t1 = a + b`

```c
(+, a, b, t1)
```

- Example 2: For expression `-(a * b) + (c * d + e)` :

This would be the generated three-address code

![Pasted image 20241116131803.png](/img/user/media/Pasted%20image%2020241116131803.png)


And this would be it's quadruple representation :

![Pasted image 20241116131840.png](/img/user/media/Pasted%20image%2020241116131840.png)


or 

| Index | Operator | op1  | op2  | result |
| ----- | -------- | ---- | ---- | ------ |
| 0     | `*`      | `a`  | `b`  | `t1`   |
| 1     | `-`      | `t1` |      | `t2`   |
| 2     | `*`      | `c`  | `d`  | `t3`   |
| 3     | `+`      | `t3` | `e`  | `t4`   |
| 4     | `+`      | `t2` | `t4` | `t5`   |

or an even better explanation :

![Pasted image 20241116133303.png](/img/user/media/Pasted%20image%2020241116133303.png)

---
### 2. Triples

- **Each instruction is represented as a tuple of three fields, without a direct result name**.
  
```c
(operator, arg1, arg2)
```

- Example: For `t1 = a + b` followed by `t2 = t1 * c`
  
```c
(1) (+, a, b)
(2) (*, (1), c)
```

- Example 2: For expression `-(a * b) + (c * d + e)` :

![Pasted image 20241116133622.png](/img/user/media/Pasted%20image%2020241116133622.png)

or

| Index | Operator | op1 | op2 |
| ----- | -------- | --- | --- |
| 0     | `*`      | `a` | `b` |
| 1     | `-`      | (0) |     |
| 2     | `*`      | `c` | `d` |
| 3     | `+`      | (2) | `e` |
| 4     | `+`      | (1) | (3) |

The values like (0), (1), (2) and (3) are **pointers which point to that specific instruction's memory location**.

---
#### Explanation:

1. **Index 0**: `a * b` is computed, and its result is stored at `(0)`.
2. **Index 1**: The negation operator (`-`) is applied to the result at `(0)`. This means that instruction 1 retrieves the result produced by instruction 0 and applies the negation.
3. **Index 2**: `c * d` is computed, and its result is stored at `(2)`.
4. **Index 3**: The addition `c * d + e` is computed using the result at `(2)` and the operand `e`.
5. **Index 4**: Finally, the addition of `-(a * b)` (result at `(1)`) and `(c * d + e)` (result at `(3)`) is computed.
---
#### Pointers in Triples:

- **Indexes like `(0)` or `(2)` refer to the results of the respective instructions**. These are implicit pointers, meaning the actual data resides in temporary memory locations, and the triple simply points to them.
- When generating the machine or assembly code later, these pointers will be translated into actual memory locations, registers, or stack offsets.
---

![Pasted image 20241116134509.png](/img/user/media/Pasted%20image%2020241116134509.png)

---
### Problem with Triples and Execution Order

For example if we were to execute instruction (2) first, it will be assigned as instruction (0) now, and it's value in instruction (1) which is supposed to be -(0) (expected `-a*b`), now becomes (`-c*d`) instead.

In the triples representation:

- Operands such as `(0)` or `(2)` refer to **the index of the instruction in the triples table**.
- The order of execution must strictly follow the sequence given in the table. If the order changes during code generation or optimization, **the meaning of the references could change**, leading to incorrect results.

---
#### Example: Reordering in the Table

##### Original Table:

| **Index** | **Operator** | **op1** | **op2** |
| --------- | ------------ | ------- | ------- |
| 0         | `*`          | `a`     | `b`     |
| 1         | `-`          | `(0)`   |         |
| 2         | `*`          | `c`     | `d`     |
| 3         | `+`          | `(2)`   | `e`     |
| 4         | `+`          | `(1)`   | `(3)`   |

Here:

- Instruction `(0)` computes `a * b`.
- Instruction `(1)` uses `(0)` to compute `-(a * b)`.

---

##### If Instructions are Executed Out of Order (e.g., `(2)` before `(0)`):

| **Index** | **Operator** | **op1** | **op2** |
| --------- | ------------ | ------- | ------- |
| 0         | `*`          | `c`     | `d`     |
| 1         | `-`          | `(0)`   |         |
| 2         | `*`          | `a`     | `b`     |
|           |              |         |         |

Here’s what happens:

- The result of `(1)` is now `-(c * d)` instead of `-(a * b)`, which is **wrong**.
- The **dependency on instruction indexes** makes triples highly sensitive to execution order.

---
### Why This Happens

- In triples, references like `(0)` are **positional**, not semantic. They assume the instructions will be executed in the **exact order** listed in the table.
- Reordering instructions during optimization or due to parallelism can break this assumption.

---
### Solutions to Avoid This Issue

#### 1. **Stick to Fixed Order During Execution**

- The simplest solution is to execute instructions in the order they appear in the triples table. However, this limits optimization opportunities (e.g., moving independent instructions for better performance).

#### 2. **Use Quadruples Instead**

- In quadruples, instead of relying on **positional references** like `(0)`, we use **explicit temporary variables** (e.g., `t1`, `t2`). For example:

```c
t1 = a * b
t2 = -t1
t3 = c * d
t4 = t3 + e
t5 = t2 + t4
```

- Since each intermediate result has a unique name (`t1`, `t2`, etc.), execution order does not affect correctness.

#### 3. **Static Single Assignment (SSA) Form**

- Another alternative is to use SSA form, where each intermediate variable is assigned only once. This makes dependencies clear and prevents ambiguity.

#### 4. **Include Dependencies in Triple Representation**

- Instead of relying on indexes, triples could explicitly track dependencies between instructions (e.g., a dependency graph). However, this complicates implementation.

---
### 3. Indirect Triples

Indirect triples are a variation of the **triples representation**, introduced to address some of the limitations of direct triples, especially the **order-dependency issue** that I raised earlier.

#### How Indirect Triples Work

- Instead of referencing instructions using **positional indices**, an **additional table** (called a pointer table or index table) is used to store pointers to the actual triples.
- Each entry in the pointer table points to a specific triple in the triples table.
- By using this intermediate layer of indirection, **reordering of instructions becomes feasible** without breaking references.

---
#### Structure of Indirect Triples

1. **Pointer Table**:
    
    - ==This table contains entries that point to the triples table==.
    - ==Each pointer can be reordered without changing the underlying triples==.
      
2. **Triples Table**:
   
    - Contains the actual instructions in the for

---
#### **Example**

Let’s use the same expression as before:  
`-(a * b) + (c * d + e)`

#### **Step 1: Triples Table**

|**Index**|**Operator**|**op1**|**op2**|
|---|---|---|---|
|0|`*`|`a`|`b`|
|1|`-`|(0)||
|2|`*`|`c`|`d`|
|3|`+`|(2)|`e`|
|4|`+`|(1)|(3)|

---

#### **Step 2: Pointer Table**

| **Pointer Index** | **Points to Triple Index** |
| ----------------- | -------------------------- |
| 100               | 0                          |
| 101               | 1                          |
| 102               | 2                          |
| 103               | 3                          |
| 104               | 4                          |


![Pasted image 20241116140413.png](/img/user/media/Pasted%20image%2020241116140413.png)


These pointers store the locations to the pointer instructions within the triples table.

**The drawback for this type of representation is that it uses twice the memory for the representation since there are two sets of pointers being used per instruction**.

![Pasted image 20241116142045.png](/img/user/media/Pasted%20image%2020241116142045.png)

Now, let's say we shuffle the order of execution in the pointer table. Will we still get the original expression?

![Pasted image 20241116142255.png](/img/user/media/Pasted%20image%2020241116142255.png)

So yeah, we still get the same expression.

---
