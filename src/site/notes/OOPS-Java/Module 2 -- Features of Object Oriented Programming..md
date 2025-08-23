---
{"dg-publish":true,"permalink":"/oops-java/module-2-features-of-object-oriented-programming/","title":"Features of OOPS -- Object Oriented Programming - Java","tags":["Semester-5","Java"],"created":"2025-03-06T18:33:28.626+05:30"}
---


---
# Index

1. [[#1. Encapsulation]]
2. [[#2. Object Identity]]
3. [[#3. Polymorphism]]
---
# 1. Encapsulation:

Encapsulation is the concept of bundling the data (variables) and methods (functions) that operate on the data into a single unit, typically a **class**. It restricts direct access to some of an object’s components, which is a means of preventing accidental or unauthorized interference.

In simple terms:

- **Data Hiding**: Encapsulation protects the internal state of an object from unwanted or incorrect modification by restricting direct access.
- **Access Control**: We control access through access modifiers like `private`, `protected`, and `public`.

**Example**:

```java
class Account {
    private double balance;  // Data is hidden using private access modifier

    public Account(double initialBalance) {
        balance = initialBalance;
    }

    // Method to get balance
    public double getBalance() {
        return balance;
    }

    // Method to deposit money (with validation)
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    // Method to withdraw money (with validation)
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }
}
```
---
In this example:

- The `balance` variable is private, so it can't be accessed directly from outside the class.
- We use methods like `deposit` and `withdraw` to modify the balance, ensuring that all modifications are controlled and validated.
---
# 2. Object Identity:

==Object identity refers to the property that each object has a unique identity, even if two objects contain the same data==. This is a core feature of OOP **because each object is distinct from others in memory, regardless of whether its content (state) is the same as that of another object**.

- In Java, object identity is typically represented by **memory address**.
- The `==` operator checks **reference equality** (whether two references point to the same object in memory), whereas the `.equals()` method can be overridden to check **logical equality** (whether two objects are logically equivalent).

Example:

```java
Account acc1 = new Account(1000);
Account acc2 = new Account(1000);

// Check object identity
System.out.println(acc1 == acc2);  // false (they are different objects)

// Check logical equality (assuming we override equals method)
System.out.println(acc1.equals(acc2));  // Depends on how equals is defined
```
Even though `acc1` and `acc2` may have the same balance, they are two different objects in memory. Hence, `acc1 == acc2` will return `false`.

---
# 3. Polymorphism:

Polymorphism means "many forms." In OOP, polymorphism allows objects of different classes to be treated as objects of a common superclass. There are two types of polymorphism in Java:

- **Compile-time polymorphism (Method Overloading)**: ==When multiple methods in the same class have the same name but different parameter lists (signature)==.
    
- **Run-time polymorphism (Method Overriding)**: When a subclass provides a specific implementation of a method that is already defined in its superclass. This happens through **inheritance**.

---
**Method Overloading Example**:

```java
class Calculator {
    // Overloaded methods
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }
}

```

Here we can see that there are two methods with the same name **double**, but their **signatures** or parameters, datatypes are different.

---
**Method Overriding Example**:

```java
class Animal {
    public void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class TestPolymorphism {
    public static void main(String[] args) {
        Animal myDog = new Dog();  // Polymorphism: a Dog object is treated as an Animal
        myDog.sound();  // Calls the overridden method in Dog class, output: "Dog barks"
    }
}
```

Here we see that the class **Dog**, inherits the method **sound** from it's parent class **Animal** but it changes the contents of the parent's method with it's own code, thus **overriding the method**.

This falls under inheritance which shall be further discussed **in detail** in module 3.

---
