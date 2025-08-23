---
{"dg-publish":true,"permalink":"/compiler-design/module-5-type-checking/","title":"Type Checking -- Compiler Design","tags":["Semester-5"],"created":"2025-03-06T18:33:20.266+05:30"}
---


---
# Index

1. [[#1. Type Systems]]
2. [[#2. Specification of a Type Checker]]

---
# 1. Type Systems

A **type system** defines rules by which a programming language associates data types with variables and expressions. It ensures that operations on these variables are **type-safe**, meaning that they are performed on compatible data types to avoid errors during program execution.

#### **Purpose of a Type System**:

- To **detect errors** (such as mismatched types) early, ideally at compile-time.
- To **prevent invalid operations**, such as trying to add a string to an integer.
- To ensure that the program executes **safely** and **correctly** with respect to types.

#### **Key Concepts**:

1. **Static Typing vs Dynamic Typing**:
    
    - **Static Typing**: Types are checked at compile-time. For example, in languages like C, Java, and C++, variables have a defined type that cannot change.
        - **Example**: In Java, if `int x = 5;`, you cannot later assign `x = "hello";` because the type is checked before the program runs.
        
    - **Dynamic Typing**: Types are checked at runtime. In languages like Python and JavaScript, variables can hold values of any type, and their types are determined during execution.
        - **Example**: In Python, `x = 5; x = "hello";` is valid since types are checked dynamically.
        
2. **Strong Typing vs Weak Typing**:
    
    - **Strong Typing**: A language is strongly typed if it restricts implicit type conversions between incompatible types. Errors are more likely to be caught early.
        - **Example**: In Python, `5 + "hello"` will raise a type error.
    - **Weak Typing**: A language is weakly typed if it allows implicit type conversions. This can lead to unexpected behavior.
        - **Example**: In JavaScript, `5 + "10"` will result in the string `"510"`, as the number is implicitly converted to a string.
        
3. **Primitive Types**:
    
    - These are the basic building blocks of data types, such as `int`, `float`, `char`, `bool`. Different languages provide their own set of primitive types.
    - **Example**: `int x = 5;` declares a primitive integer type in C.
    - 
4. **Composite Types**:
    
    - Composite types are formed by combining primitive types. Common examples include **arrays**, **structures (records)**, **pointers**, and **unions**.
    - **Example**: In C, `struct Point { int x; int y; }` defines a composite type called `Point`.
    
5. **Type Inference**:
    
    - Some languages automatically determine the type of a variable based on its value. This is often used in functional programming languages like Haskell or Scala.
    - **Example**: In Haskell, `let x = 5` infers that `x` is of type `Int` because of the integer value assigned to it.
    
6. **Type Errors**:
    
    - **Type mismatch**: This occurs when an operation is performed on incompatible types.
        - **Example**: Trying to add a string and an integer in C (`int + char*`) will result in a type error.
    - **Undeclared variables**: Using a variable without declaring its type (in statically-typed languages) will cause an error.
    
7. **Type Safety**:
    
    - A language is **type-safe** if it prevents type errors during execution. This ensures that each operation only applies to compatible types, protecting against invalid memory accesses or runtime crashes.

---
# 2. Specification of a Type Checker

A **type checker** is responsible for verifying that a program follows the type rules of the language and is type-safe. The **type checker** examines the source code to ensure that the variables, expressions, and functions operate on compatible types. If type inconsistencies are found, it reports errors, ensuring that the program does not proceed with invalid type operations.

In **Compiler Design**, type checking is part of the **semantic analysis** phase, which happens after parsing.

#### **Key Components of a Type Checker**:

1. **Type Expressions**:
    
    - Type expressions represent the type of a language construct. Common types include:
        - **Primitive types** like `int`, `float`, `char`, `bool`.
        - **Constructed types** such as arrays (`int[]`), functions (`int -> int`), pointers (`int*`), and user-defined types (`struct` or `class`).

---
2. **Type Rules**:
    
    - The type checker applies type rules, which define valid operations and conversions between types.
    - For example, a type rule might state that only numbers can be added:
```mathematica
int + int = int
float + float = float
int + float = float
```
---
3. **Type Environment (Context)**:

- The **type environment** is a mapping of variables to their respective types in the current scope. For example, in the code:
```c
int x = 5;
float y = 3.14;
```
- The type environment would store:  
    `x -> int`  
    `y -> float`
- The type checker uses the type environment to verify the validity of variable usage and assignments.
---
#### **Steps in the Type Checking Process**:

1. **Initialize the Type Environment**:
    
    - The type checker begins by initializing an environment where each declared variable, function, or expression is associated with its type.
    
2. **Traverse the Abstract Syntax Tree (AST)**:
    
    - The type checker processes the **Abstract Syntax Tree (AST)** produced during parsing. Each node of the AST represents a language construct (e.g., an expression or statement).
    - The type checker recursively checks each node to ensure that all types are consistent.
    
3. **Check Type Consistency**:
    
    - For each node in the AST, the type checker applies the language’s type rules. For example:
        - **Expressions**: The type checker ensures that arithmetic and logical expressions involve compatible types (e.g., adding two numbers, comparing two booleans).
        - **Assignments**: The type checker verifies that the right-hand side of an assignment is of the same type as the left-hand side (i.e., you cannot assign a string to an integer).
        - **Function Calls**: The type checker verifies that the number and types of arguments match the function’s signature.
        - **Control Structures**: It checks that conditions in `if`, `while`, and `for` statements are boolean expressions.
        
4. **Handle Type Conversions (if applicable)**:
    
    - In some languages, **implicit type conversions** (coercions) are allowed. For example, assigning an `int` to a `float` may be valid if the language allows such a conversion. The type checker ensures that these conversions are safe and valid.

---
### **Example of Type Checking**:

Consider the following code in a simple C-like language:

```c
int x = 5;
float y = 3.14;
x = y + 2;
if (x < 10) {
    x = x + 1;
}
```

**Step 1: Initialize the Type Environment**:

- After analyzing the declarations:

```c
x -> int
y -> float
```
- **Step 2: Traverse and Type Check**:
    
    - For the expression `y + 2`, the type checker sees that `y` is a `float` and `2` is an `int`. Since `int + float = float`, it assigns the result to a temporary float.
    - When `x = y + 2` is encountered, the type checker notices that `x` is `int` and `y + 2` is `float`, which is an incompatible assignment. This raises a **type mismatch error** unless the language allows implicit conversion.
- **Step 3: Check Control Structures**:
    
    - In the condition `x < 10`, the type checker ensures that `x` is an integer and `10` is also an integer. Since both types are compatible for comparison, it proceeds.

#### **Algorithm for a Type Checker**:

1. **Input**: AST of the program, type rules, and type environment.
2. **Output**: Type errors (if any) or a successful type check.

**Procedure**:

1. Traverse each node in the AST.
2. For each node, apply the type rules to the associated types.
3. Update the type environment as needed (e.g., when encountering variable declarations).
4. Propagate types from children to parent nodes (for synthesized attributes).
5. Report errors if type mismatches or invalid operations are detected.

---
