---
{"dg-publish":true,"permalink":"/oops-java/module-1-abstract-data-types-and-their-specification/","title":"Abstract Data Types -- Object Oriented Programming - Java","tags":["Semester-5","Java"],"created":"2025-03-06T18:33:28.607+05:30"}
---


---
# Index

1. [[#Introduction to Abstract Data Types (ADTs)]]
2. [[#Concrete Invariants and Abstraction Functions]]

----
# Introduction to Abstract Data Types (ADTs)

An **Abstract Data Type (ADT)** is a way of defining a data structure abstractly, focusing on _what it does_ rather than _how it does it_. The key idea is to separate the _interface_ of the data type (what operations are available) from the _implementation_ (how the data is stored and how the operations are carried out).

#### **Key Concepts of ADTs:**

1. **Operations**: ADTs specify operations that can be performed, without specifying how those operations are implemented. For example, a `Stack` ADT might support operations like:
    
    - `push(x)`: Add an element `x` to the stack.
    - `pop()`: Remove and return the top element.
    - `peek()`: Look at the top element without removing it.
2. **Encapsulation**: ADTs hide the internal details of the data structure, ensuring that the user only interacts with the data via defined operations. This allows for flexibility in changing the implementation without affecting the user's experience.
    
3. **Concrete State** vs **Abstract State**:
    
    - **Concrete State**: The actual, physical way the data is stored in memory (e.g., array, linked list).
    - **Abstract State**: How the data is perceived or understood by the user, regardless of the underlying implementation (e.g., a stack of integers).

#### **Benefits of Using ADTs**:

- **Modularity**: By using ADTs, you can work with higher-level concepts and write modular code. You don’t need to know the internal details to use the ADT.
- **Reusability**: Once you define an ADT, it can be reused across different programs without needing to know its underlying implementation.
- **Maintainability**: Changes in the implementation of an ADT do not affect the rest of the codebase that relies on it.

### **Example: Stack ADT**

Let’s start with the **Stack ADT** as an example to understand these concepts better.

#### **Stack ADT Operations**:

- **push(x)**: Inserts element `x` at the top of the stack.
- **pop()**: Removes the top element and returns it.
- **peek()**: Returns the top element without removing it.
- **isEmpty()**: Checks if the stack is empty.
- **size()**: Returns the number of elements in the stack.

#### **Abstract View**:

From the user's perspective, the stack can be visualized as:

```css
Top -->  [element3]
         [element2]
         [element1]  <-- Bottom
```

The user interacts with the stack only through the provided operations (`push`, `pop`, etc.), and they don’t need to worry about how the stack is implemented internally.

---
### **Concrete Implementation of Stack (Array-based)**

Let’s look at how we can implement this stack in Java using an **array**. This will help illustrate the **concrete state** of the stack.

```java
public class Stack {
    private int[] arr;
    private int top;
    private int capacity;
    
    // Constructor to initialize the stack
    public Stack(int size) {
        arr = new int[size];
        capacity = size;
        top = -1;  // Stack is initially empty
    }
    
    // Push method to add elements to the stack
    public void push(int x) {
        if (isFull()) {
            System.out.println("Stack Overflow");
            return;
        }
        arr[++top] = x;
    }
    
    // Pop method to remove and return the top element
    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack Underflow");
            return -1;
        }
        return arr[top--];
    }
    
    // Peek method to view the top element without removing it
    public int peek() {
        if (!isEmpty()) {
            return arr[top];
        } else {
            System.out.println("Stack is empty");
            return -1;
        }
    }
    
    // Method to check if the stack is empty
    public boolean isEmpty() {
        return top == -1;
    }
    
    // Method to check if the stack is full
    public boolean isFull() {
        return top == capacity - 1;
    }
    
    // Method to get the size of the stack
    public int size() {
        return top + 1;
    }
}
```
#### **Explanation**:

- **Concrete State Space**: The stack uses an `int[] arr` array to store elements. The integer `top` tracks the index of the top element in the stack. This is the **concrete representation** of the stack.
- **Abstraction Function**: The abstraction function here would map the `arr` array and `top` index to a stack of elements. For example, if `top = 2` and `arr = [5, 10, 20]`, the abstract state of the stack is:

```css
Top --> [20]
        [10]
        [5]  <-- Bottom
```
---
# Concrete Invariants and Abstraction Functions

#### **Concrete Invariants**:

Concrete invariants are conditions that must always hold true for the concrete state of an ADT during its lifetime. They ensure that the data structure is always in a valid state. In the example of the **Stack ADT**:

- **Invariant 1**: `top >= -1` and `top < capacity`
    - This ensures that the `top` pointer always points to a valid index in the array.
    - When `top == -1`, it indicates that the stack is empty.
- **Invariant 2**: The stack must never overflow beyond its capacity.
    - This is enforced by checking if `top == capacity - 1` before pushing a new element, which ensures that no more elements can be added if the stack is full.

These invariants help in maintaining the correctness of the stack. If any of these conditions are violated, the stack would not function properly.

===**Concrete invariants** are the rules or constraints that define the valid states for the concrete implementation of an ADT. These constraints ensure that the data structure operates correctly and remains in a consistent state throughout its use===.

---
#### **Abstraction Functions**:

The **abstraction function** bridges the gap between the concrete representation of the data and its abstract view. It defines how the **concrete state** (the actual values stored and pointers used) maps to the **abstract state** (what the user perceives).

For the **Stack ADT**, the abstraction function is defined as:

- Given an array `arr` and an index `top`, the abstract state is the stack containing the elements `arr[0]` to `arr[top]`.
- The top element of the stack is `arr[top]` if `top >= 0`, and the stack is empty if `top == -1`.

This function hides the implementation details (like using an array and a `top` index) from the user. They only see the abstract behavior of pushing and popping elements in a stack.

---
#### **Example: Stack ADT with Concrete Invariants and Abstraction Function**

Let’s revisit the array-based **Stack ADT** we implemented, but now we’ll formally define its **invariants** and **abstraction function**.

1. **Concrete State**:
    
    - The stack is represented by the array `arr[]` and the integer `top`.
2. **Concrete Invariants**:
    
    - `-1 <= top < capacity`
    - The stack contains elements from `arr[0]` to `arr[top]`.
3. **Abstraction Function**:
    
    - If `top == -1`: the stack is empty.
    - If `top >= 0`: the stack contains elements `arr[0], arr[1], ..., arr[top]` in order, with `arr[top]` being the topmost element.

Here’s how we can express these ideas in code comments to reinforce the concepts:

```java
public class Stack {
    private int[] arr;  // The array storing the elements of the stack
    private int top;    // Index of the top element in the stack
    private int capacity;  // Maximum capacity of the stack

    // Invariant: -1 <= top < capacity
    // Abstraction function: 
    //   If top == -1, the stack is empty.
    //   If top >= 0, the stack contains arr[0] to arr[top], with arr[top] as the top element.
    
    // Constructor to initialize the stack
    public Stack(int size) {
        arr = new int[size];
        capacity = size;
        top = -1;  // Stack is initially empty
    }

    // Push method to add elements to the stack
    public void push(int x) {
        if (isFull()) {
            System.out.println("Stack Overflow");
            return;
        }
        arr[++top] = x;  // Increment top and add the element to the top position
    }

    // Pop method to remove and return the top element
    public int pop() {
        if (isEmpty()) {
            System.out.println("Stack Underflow");
            return -1;
        }
        return arr[top--];  // Return the top element and decrement top
    }

    // Peek method to view the top element without removing it
    public int peek() {
        if (!isEmpty()) {
            return arr[top];
        } else {
            System.out.println("Stack is empty");
            return -1;
        }
    }

    // Method to check if the stack is empty
    public boolean isEmpty() {
        return top == -1;  // Invariant: -1 <= top
    }

    // Method to check if the stack is full
    public boolean isFull() {
        return top == capacity - 1;  // Invariant: top < capacity
    }

    // Method to get the size of the stack
    public int size() {
        return top + 1;  // Size is top + 1 (since top is 0-based)
    }
}
```
---
