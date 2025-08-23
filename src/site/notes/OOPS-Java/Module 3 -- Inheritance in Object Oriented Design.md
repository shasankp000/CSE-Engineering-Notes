---
{"dg-publish":true,"permalink":"/oops-java/module-3-inheritance-in-object-oriented-design/","title":"Inheritance in OOPS -- Object Oriented Programming - Java","tags":["Semester-5","Java"],"created":"2025-03-06T18:33:28.629+05:30"}
---


---
# Index

1. [[#1. Inheritance in Object-Oriented Design]]
2. [[#2. Design Patterns Introduction and Classification]]
3. [[#3. Iterator Pattern]]
---
# 1. Inheritance in Object-Oriented Design:

Inheritance allows one class (called the **subclass** or **derived class**) to inherit the fields and methods of another class (called the **superclass** or **base class**). This promotes **code reuse** and establishes a natural **hierarchy** between classes.

- **Superclass**: The parent class from which properties and methods are inherited.
- **Subclass**: The child class that inherits from the superclass.

**Key Concepts**:

- A subclass **inherits** all non-private members (fields and methods) of its superclass.
- Subclasses can **override** methods of the superclass to provide a more specific implementation.
- In Java, inheritance is implemented using the `extends` keyword.

**Example**:

```java
class Animal {
    protected String name;

    public void eat() {
        System.out.println("This animal eats food.");
    }
}

class Dog extends Animal {  // Inherits from Animal
    public Dog(String name) {
        this.name = name;  // Inherited from Animal
    }

    @Override
    public void eat() {
        System.out.println(name + " eats dog food.");  // Overridden method
    }
}
```

In this example:

- The `Dog` class **inherits** the `name` field and `eat()` method from the `Animal` class.
- The `Dog` class **overrides** the `eat()` method to give a more specific behavior.

##### **Benefits of Inheritance**:

- **Code Reusability**: You don't need to rewrite common methods for each subclass.
- **Extensibility**: Subclasses can extend the functionality of a superclass while still reusing its code.
- **Method Overriding**: Allows you to provide a subclass-specific implementation of a method while maintaining a common interface.
---

# 2. Design Patterns: Introduction and Classification

Design patterns are typical solutions to common problems in software design. They represent **best practices** and provide general templates that can be applied to solve recurring design challenges.

##### **Introduction to Design Patterns**:

- **Creational Patterns**: Deal with object creation mechanisms, trying to create objects in a manner suitable for the situation. Examples include **Singleton** and **Factory** patterns.
- **Structural Patterns**: Focus on how objects and classes are composed to form larger structures. Examples include **Adapter**, **Decorator**, and **Composite** patterns.
- **Behavioral Patterns**: Deal with object collaboration and interaction. Examples include **Observer**, **Strategy**, and **Iterator** patterns.

##### **Classification of Design Patterns**:

1. **Creational Patterns**:
    
    - Focus on how objects are created.
    - Example: **Factory Pattern**, **Singleton Pattern**.
2. **Structural Patterns**:
    
    - Deal with object composition, forming larger structures.
    - Example: **Adapter Pattern**, **Composite Pattern**.
3. **Behavioral Patterns**:
    
    - Focus on how objects interact with one another.
    - Example: **Observer Pattern**, **Iterator Pattern**.

---
# 3. Iterator Pattern:

The **Iterator pattern** is a **behavioral design pattern** that provides a way to access elements of a collection (like a list or array) sequentially without exposing the underlying representation.

**Why Use the Iterator Pattern?**

- It decouples the client from the underlying structure of the collection.
- The client can focus on **traversing** the collection without worrying about how the collection is internally implemented.

**Example**:

```java
import java.util.Iterator;
import java.util.ArrayList;

class Main {
    public static void main(String[] args) {
        ArrayList<String> animals = new ArrayList<>();
        animals.add("Cat");
        animals.add("Dog");
        animals.add("Cow");

        // Using an iterator to traverse the collection
        Iterator<String> iterator = animals.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
    }
}
```

In this example:

- An `ArrayList` of animals is created.
- The `Iterator` is used to traverse the list without exposing the internal structure of `ArrayList`.

##### **Benefits of the Iterator Pattern**:

- Provides a standard way to loop through different types of collections.
- Makes code cleaner and easier to maintain.

---
