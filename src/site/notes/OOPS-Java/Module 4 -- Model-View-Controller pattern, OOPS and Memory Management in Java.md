---
{"dg-publish":true,"permalink":"/oops-java/module-4-model-view-controller-pattern-oops-and-memory-management-in-java/","title":"MVC and memory management in OOPS -- Object Oriented Programming - Java","tags":["Semester-5","Java"],"created":"2025-03-06T18:33:28.645+05:30"}
---


---
# Index

1. [[#1. Model-View-Controller (MVC) Pattern]]
2. [[#2. Commands as Methods and as Objects]]
3. [[#3. Implementing Object-Oriented Language Features]]
4. [[#4. Memory management in Java]]
---
# 1. Model-View-Controller (MVC) Pattern:

The **Model-View-Controller** (MVC) design pattern is a widely used pattern for creating user interfaces. It helps separate concerns into three interconnected components:

- **Model**: The core component, responsible for managing the data, logic, and rules of the application.
- **View**: The visual representation of the model’s data (UI).
- **Controller**: The intermediary between Model and View. It handles the user input and updates the Model accordingly.

##### **How MVC Works**:

1. **User Interaction**: The user interacts with the **View** (UI), for example, by clicking a button.
2. **Controller Response**: The **Controller** handles this input and translates it into an action for the **Model**.
3. **Model Update**: The **Model** updates its data based on the action.
4. **View Update**: Once the **Model** changes, the **View** updates itself to reflect the new data.

**Example**:

Imagine a simple text editor. The **Model** holds the text, the **View** displays the text, and the **Controller** handles user input like adding or deleting characters.

![MVC.png](/img/user/media/MVC.png)

---
# 2. Commands as Methods and as Objects:

In object-oriented programming, commands can be handled in two primary ways:

- **Commands as Methods**: This is when you use methods (functions) to encapsulate a command or action.
- **Commands as Objects**: This is when you represent commands as separate objects (using the **Command Pattern**). Each command is represented as an object that encapsulates the action and the information needed to perform that action.

##### **Command Pattern**:

The **Command Pattern** is a behavioral design pattern that turns a request into a stand-alone object containing all the information about the request. It allows you to parameterize objects with operations, delay execution, queue operations, and support undoable operations.

Example :

```java
// Command interface
interface Command {
    void execute();
}

// Receiver class
class Light {
    public void turnOn() {
        System.out.println("Light is on");
    }

    public void turnOff() {
        System.out.println("Light is off");
    }
}

// Concrete command classes
class TurnOnCommand implements Command {
    private Light light;

    public TurnOnCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOn();
    }
}

class TurnOffCommand implements Command {
    private Light light;

    public TurnOffCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOff();
    }
}

public class Main {
    public static void main(String[] args) {
        // Create a receiver
        Light light = new Light();
        
        // Create command objects
        Command turnOn = new TurnOnCommand(light);
        Command turnOff = new TurnOffCommand(light);
        
        // Create the invoker
        RemoteControl remote = new RemoteControl();
        
        // Set the command to "turn on" and execute it
        remote.setCommand(turnOn);
        remote.pressButton();  // Output: Light is on
        
        // Set the command to "turn off" and execute it
        remote.setCommand(turnOff);
        remote.pressButton();  // Output: Light is off
    }
}

```
---
### Code example for Commands encapsulated as methods :

This version will encapsulate the logic for turning the light on and off inside a single `RemoteControl` class, with methods representing commands instead of separate command classes.

```java
// Receiver: Light
class Light {
    public void turnOn() {
        System.out.println("Light is on");
    }

    public void turnOff() {
        System.out.println("Light is off");
    }
}

// Invoker: RemoteControl
class RemoteControl {
    private Light light;

    public RemoteControl(Light light) {
        this.light = light;
    }

    // Command methods encapsulated inside the RemoteControl class
    public void pressOnButton() {
        light.turnOn();
    }

    public void pressOffButton() {
        light.turnOff();
    }
}

// Client: Main class
public class Main {
    public static void main(String[] args) {
        // Create the receiver
        Light light = new Light();
        
        // Create the invoker with the light receiver
        RemoteControl remote = new RemoteControl(light);
        
        // Now we use methods instead of command objects
        remote.pressOnButton();  // Output: Light is on
        remote.pressOffButton(); // Output: Light is off
    }
}
```
### **How It Works:**

- The `Light` class is the **receiver** with its own actions (`turnOn()` and `turnOff()` methods).
- The `RemoteControl` class encapsulates the **commands** as methods (`pressOnButton()` and `pressOffButton()`), which internally call the appropriate methods on the `Light` receiver.
- In the `main` method, the `RemoteControl` object is instantiated with a `Light` object, and the button presses invoke the appropriate commands.

### **Key Differences**:

1. **No Command Interface or Separate Command Classes**: Instead of having separate `TurnOnCommand` and `TurnOffCommand` classes that implement an interface, the commands are **encapsulated as methods** within the `RemoteControl` class itself.
2. **Direct Method Invocation**: When the user presses a button on the remote, the corresponding method (`pressOnButton()` or `pressOffButton()`) is directly invoked to perform the command. This simplifies the structure, but you lose some of the flexibility and extensibility that the **command pattern** provides.

### **When to Use This Approach:**

- This method-based encapsulation works well for simpler use cases where you don’t need the flexibility to easily add new commands or change behavior at runtime.
- If you anticipate many different commands, or if the commands need to be passed around as objects (such as in a queue, or for undo/redo functionality), then the **command pattern** with separate command classes would be more appropriate.

---
# Summary of Method Encapsulation vs. Command Pattern:

- **Method Encapsulation**: Simpler, direct method calls without needing separate classes. This works well for cases where you have fewer commands or don't need to change command behavior dynamically.
- **Command Pattern** (previous example): More flexible as it decouples the request from the action, allowing for easier modification of behavior, dynamic assignment of commands, and additional features like undo/redo.
---
# 3. Implementing Object-Oriented Language Features:

This section explores some key language features that are part of OO programming:

1. **Abstraction**: Focuses on exposing only relevant details while hiding the complexity of the internal implementation.
    
    - **Example**: Abstract classes and interfaces in Java.
2. **Encapsulation**: Bundles data (fields) and methods operating on the data into a single unit (class) and restricts access to some of the object’s components.
    
    - **Example**: Declaring class members as `private` and providing `public` getter/setter methods.
3. **Polymorphism**: The ability to treat objects of different classes in the same way, typically using inheritance or interfaces.
    
    - **Example**: Method overloading and overriding.
4. **Inheritance**: Allows one class to inherit fields and methods from another, promoting code reuse.
    
    - **Example**: `extends` keyword in Java.
5. **Composition**: Involves building complex objects by combining simpler ones. Unlike inheritance, composition doesn’t involve a parent-child relationship.
    
    - **Example**: A class having an instance of another class as a field.

### Comprehensive code example:

- A **base class** (`Animal`) to represent shared characteristics and behavior (abstraction and inheritance).
- **Derived classes** (`Dog` and `Cat`) to represent specific animals (inheritance and polymorphism).
- Encapsulated data (like `name` and `age`).
- Use of **polymorphism** to demonstrate overriding behavior.

```java
// Abstraction: Abstract base class Animal
abstract class Animal {
    // Encapsulation: Private variables with getters/setters
    private String name;
    private int age;

    // Constructor to initialize common attributes
    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Abstract method for sound (will be overridden by subclasses)
    public abstract void makeSound();

    // Getter and Setter for encapsulated fields
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    // Concrete method shared by all animals
    public void eat() {
        System.out.println(name + " is eating.");
    }
}

// Inheritance: Derived class Dog
class Dog extends Animal {
    // Constructor for Dog class
    public Dog(String name, int age) {
        super(name, age);  // Calls the constructor of the base class
    }

    // Polymorphism: Overriding the makeSound method for Dog
    @Override
    public void makeSound() {
        System.out.println(getName() + " barks: Woof Woof!");
    }
}

// Inheritance: Derived class Cat
class Cat extends Animal {
    // Constructor for Cat class
    public Cat(String name, int age) {
        super(name, age);  // Calls the constructor of the base class
    }

    // Polymorphism: Overriding the makeSound method for Cat
    @Override
    public void makeSound() {
        System.out.println(getName() + " meows: Meow Meow!");
    }
}

// Main class to demonstrate OOP concepts
public class Main {
    public static void main(String[] args) {
        // Creating objects of derived classes
        Animal dog = new Dog("Buddy", 5);
        Animal cat = new Cat("Whiskers", 3);

        // Encapsulation: Using getters to access private fields
        System.out.println(dog.getName() + " is " + dog.getAge() + " years old.");
        System.out.println(cat.getName() + " is " + cat.getAge() + " years old.");

        // Polymorphism: The makeSound method behaves differently for Dog and Cat
        dog.makeSound();  // Output: Buddy barks: Woof Woof!
        cat.makeSound();  // Output: Whiskers meows: Meow Meow!

        // Shared method from the base class (inherited behavior)
        dog.eat();  // Output: Buddy is eating.
        cat.eat();  // Output: Whiskers is eating.
    }
}

```
### **Explanation of OOP Pillars in this Program:**

1. **Encapsulation**:
    
    - The `name` and `age` attributes in the `Animal` class are **private**, meaning they can only be accessed within the class itself.
    - To interact with these private attributes, **getter** and **setter** methods are used (`getName()`, `getAge()`, `setName()`, `setAge()`), encapsulating the data and controlling how it’s accessed.
2. **Abstraction**:
    
    - The `Animal` class is an **abstract class**, meaning it provides a common blueprint for all animals, but we cannot create an `Animal` object directly.
    - It contains an **abstract method** `makeSound()` that must be implemented by all subclasses, defining a general behavior that can be customized by different types of animals.
3. **Inheritance**:
    
    - The `Dog` and `Cat` classes **inherit** from the `Animal` class, meaning they inherit its properties and behaviors (like the `eat()` method) and can also provide their own specific behaviors.
    - Both `Dog` and `Cat` share common attributes and behavior, such as `name` and `age`, through inheritance from `Animal`.
4. **Polymorphism**:
    
    - **Method Overriding**: The `Dog` and `Cat` classes **override** the `makeSound()` method of the `Animal` class to provide their own specific implementations (barking for dogs and meowing for cats).
    - The program uses the same method (`makeSound()`), but its behavior changes based on the type of object (`Dog` or `Cat`) that calls it. This demonstrates **polymorphism**.

### **How the Program Works**:

- The `Animal` class provides a general definition of an animal with common attributes and behaviors.
- `Dog` and `Cat` inherit from `Animal` but override the `makeSound()` method to provide behavior specific to each type.
- The `main()` method creates a `Dog` and a `Cat`, accesses their encapsulated data using getters, and demonstrates polymorphism by calling the same `makeSound()` method on each, with different results depending on the object type.

---
# 4. Memory management in Java

Memory management is crucial in any software development process. In Java, memory is automatically managed by the **Garbage Collector (GC)**, but it's important to understand the underlying concepts.

The **Java Memory Model (JMM)** is a part of the Java runtime environment that defines how threads interact through memory, including rules on data storage and retrieval for consistent access. It also provides a framework for handling concurrent execution, ensuring the integrity and safety of data across threads, even on multi-core systems.
### **Java Memory Model Components**

The JMM organizes memory into **three main regions**:

1. **Heap Memory**
2. **Stack Memory**
3. **Method Area**

Let’s break down each component:
#### 1. **Heap Memory**

- **Purpose**: Heap memory is the region where **all objects and class-level variables** are stored.
- **Lifecycle**: Data in the heap is accessible to all threads, making it ideal for storing data that needs to persist beyond the scope of a single method.
- **Garbage Collection**: Heap memory is managed by the garbage collector (GC), which automatically removes objects no longer in use to free up memory.
#### 2. **Stack Memory**

- **Purpose**: Stack memory holds **local variables and method calls** specific to each thread, meaning each thread has its own stack.
- **Lifecycle**: When a method is invoked, a new stack frame is created, storing its local variables and reference pointers. Once the method completes, the stack frame is destroyed, freeing up memory automatically.
- **Scope**: Stack memory is not shared between threads, ensuring **thread safety** for local variables.

#### 3. **Method Area**

- **Purpose**: Also known as **MetaSpace** in modern JVMs, the method area holds **class metadata, static variables, constants, and method code**.
- **Lifecycle**: Data here persists for as long as the class is loaded. It's a shared space accessible to all threads.

---
### **Java Memory Model and Concurrency**

The JMM specifies rules around **visibility and ordering of variables** across threads to avoid concurrency issues:

- **Visibility**: Ensures that changes made by one thread are visible to others. Java’s `volatile` keyword can enforce immediate visibility by instructing the JVM to directly access memory.
- **Ordering**: Uses a technique called **happens-before** ordering, guaranteeing that actions in one thread occur in the right sequence relative to actions in other threads.

### **Java Garbage Collection (GC)**

The **garbage collector (GC)** ==is responsible for automatic memory management, especially in the heap. The GC identifies objects that are no longer in use, deallocates them, and frees up memory to prevent memory leaks==. Java’s garbage collection is performed in multiple phases, often classified into **young generation** and **old generation** memory spaces.

#### **Memory Generation Breakdown**

1. **Young Generation**:
    
    - Divided into **Eden Space** and **Survivor Spaces** (S0 and S1).
    - **Eden Space**: Newly created objects start here. When it fills up, a **minor garbage collection** is triggered to move objects that are still in use to one of the Survivor Spaces.
    - **Survivor Spaces (S0 and S1)**: Act as intermediate spaces for objects that survive a minor GC, moving between them until they’re old enough for the old generation.
2. **Old Generation**:
    - Objects that survive multiple rounds in the young generation are promoted to the old generation.
    - When the old generation fills up, a **major garbage collection** (or full GC) is triggered, which is more intensive and can impact application performance.
3. **Permanent Generation (PermGen)** / **Metaspace**:
    
    - In older JVMs, **PermGen** was used to store class metadata, but this was replaced by **Metaspace** in Java 8 to provide a more flexible memory allocation strategy for metadata.

---
#### **Types of Garbage Collection Algorithms**

Java employs different garbage collection algorithms for optimizing memory management based on the application’s requirements:

1. **Serial GC**:
    - Best for single-threaded applications, as it uses a single thread for garbage collection.
2. **Parallel GC (Throughput Collector)**:
    - Uses multiple threads for GC in the young generation, making it suitable for high-throughput applications.
3. **CMS (Concurrent Mark-Sweep) GC**:
    - Designed for low-pause applications; performs most GC work concurrently with application threads, reducing the time the application is paused.
4. **G1 (Garbage-First) GC**:
    - Designed for larger heap sizes and provides predictable pause times by prioritizing regions with the most garbage, which optimizes collection across both young and old generations.

---
#### **Phases of Garbage Collection**

Garbage Collection is typically carried out in three phases:

1. **Mark Phase**: Identifies all reachable objects starting from the root objects, which are still accessible and in use.
2. **Sweep Phase**: Removes or “sweeps” objects that are not reachable and therefore considered garbage.
3. **Compact Phase**: Compacts the heap by moving objects to fill gaps, reducing fragmentation and optimizing memory layout.

---
### **How to Interact with the Garbage Collector**

Java provides some control over garbage collection:

- **`System.gc()`**: A request to the JVM for garbage collection, though it’s only a suggestion, not a command.
- **Finalization**: If an object overrides the `finalize()` method, it will be called before the object is collected, although this is rarely recommended in modern Java due to performance concerns.
---
