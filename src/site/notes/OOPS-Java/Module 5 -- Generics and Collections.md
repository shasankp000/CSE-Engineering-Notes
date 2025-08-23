---
{"dg-publish":true,"permalink":"/oops-java/module-5-generics-and-collections/","title":"Generics and Collections in OOPS -- Object Oriented Programming - Java","tags":["Semester-5","Java"],"created":"2025-03-06T18:33:28.658+05:30"}
---


---
# Index

1. [[#1. Introduction to Generics]]
2. [[#2. Java Collections]]
---
# 1. Introduction to Generics

**Generics** in Java allow you to write flexible, reusable code while ensuring type safety. With generics, you can define classes, interfaces, and methods where the type of data is specified at runtime, but with compile-time checks. This avoids issues like `ClassCastException` and removes the need for extensive casting.

For example, consider a simple generic class that ==holds any type of data==:

```java
public class Box<T> {
    private T item;

    public void setItem(T item) {
        this.item = item;
    }

    public T getItem() {
        return item;
    }
}
```
Here:

- `T` is a **type parameter** that stands for any data type (like `Integer`, `String`, or `CustomClass`).
- When you create an instance, you specify the type you want `T` to represent.

```java
Box<String> stringBox = new Box<>();
stringBox.setItem("Hello, Generics!");
System.out.println(stringBox.getItem());

Box<Integer> intBox = new Box<>();
intBox.setItem(123);
System.out.println(intBox.getItem());
```

This ensures type safety: you can only put a `String` in a `Box<String>` and an `Integer` in a `Box<Integer>`.

---
# 2. Java Collections

Here's a link to my Github repository for more in-depth code examples: https://github.com/shasankp000/JavaCollections

The **Collections Framework** provides a set of classes and interfaces for working with collections of objects, such as lists, sets, and maps. Key interfaces include:

- **List**: An ordered collection that allows duplicates (e.g., `ArrayList`, `LinkedList`).
- **Set**: An unordered collection that doesn’t allow duplicates (e.g., `HashSet`, `TreeSet`).
- **Map**: A collection of key-value pairs (e.g., `HashMap`, `TreeMap`).

Each collection type supports different operations, and generics enhance their flexibility and safety.

#### Key Classes in Collections Framework

1. **ArrayList**
    
    - Resizable array implementation of the `List` interface.
    - Allows duplicate elements and maintains insertion order.
```java
List<String> fruits = new ArrayList<>();
fruits.add("Apple");
fruits.add("Banana");
fruits.add("Apple"); // Allows duplicates
System.out.println(fruits); // [Apple, Banana, Apple]
```
---
2. **HashSet**

- Implements the `Set` interface, does not allow duplicate elements, and doesn’t maintain any particular order.
  
```java
Set<String> cities = new HashSet<>();
cities.add("New York");
cities.add("Los Angeles");
cities.add("New York"); // Duplicate, will not be added
System.out.println(cities); // [Los Angeles, New York]
```
---
3. **HashMap**

- Implements the `Map` interface, storing key-value pairs. 
- Keys must be unique; values can be duplicated.

```java
Map<String, Integer> ages = new HashMap<>();
ages.put("Alice", 30);
ages.put("Bob", 25);
ages.put("Alice", 35); // Overwrites the previous value for "Alice"
System.out.println(ages); // {Alice=35, Bob=25}
```
---
### 3. **Using Generics with Collections**

Generics help ensure that your collections only contain objects of a specified type. Here’s how you can use generics with the collections framework:

```java
List<String> names = new ArrayList<>();
names.add("John");
names.add("Alice");

// Uncommenting the following line would cause a compile-time error
// names.add(123);

for (String name : names) {
    System.out.println(name);
}
```
Without generics, you would have to cast objects when retrieving them from a collection, leading to potential runtime errors. Generics help catch such errors at compile time.

---
### 4. **Bounded Type Parameters**

Sometimes, you may want to restrict the types that can be used with generics to a certain hierarchy. This is where **bounded type parameters** come in.

```java
public class NumberBox<T extends Number> {  // T must be a subclass of Number
    private T number;

    public NumberBox(T number) {
        this.number = number;
    }

    public double square() {
        return number.doubleValue() * number.doubleValue();
    }
}

// Example usage:
NumberBox<Integer> intBox = new NumberBox<>(5);
System.out.println(intBox.square()); // Output: 25.0
```

Here, `T` is constrained to subclasses of `Number`, meaning `NumberBox` can be instantiated with `Integer`, `Double`, `Float`, etc., but not `String` or other types.

---
### 5. **Wildcards**

Wildcards in generics (`?`) let you create flexible methods that work with collections of different types. There are three main types of wildcards:

1. **Unbounded Wildcard (`?`)**: Allows any type.
```java
public void printList(List<?> list) {
    for (Object element : list) {
        System.out.println(element);
    }
}
```
2. **Upper Bounded Wildcard (`? extends Type`)**: Restricts to `Type` or any subclass.
```java
public double sumNumbers(List<? extends Number> numbers) {
    double sum = 0.0;
    for (Number num : numbers) {
        sum += num.doubleValue();
    }
    return sum;
}
```
3. **Lower Bounded Wildcard (`? super Type`)**: Restricts to `Type` or any superclass.

```java
public void addIntegers(List<? super Integer> list) {
    list.add(1); // Can add Integer or subclasses of Integer
}
```
---
### Putting It All Together

Here’s a complete example using a few different collection types with generics:

```java
import java.util.*;

public class GenericCollectionsExample {
    public static void main(String[] args) {
        // ArrayList with generics
        List<String> names = new ArrayList<>();
        names.add("Alice");
        names.add("Bob");

        // HashSet with generics
        Set<Integer> numbers = new HashSet<>();
        numbers.add(10);
        numbers.add(20);

        // HashMap with generics
        Map<String, Double> productPrices = new HashMap<>();
        productPrices.put("Book", 12.99);
        productPrices.put("Pen", 1.49);

        // Displaying values
        printList(names);
        System.out.println("Sum of numbers: " + sumNumbers(new ArrayList<>(numbers)));
        System.out.println("Product prices: " + productPrices);
    }

    public static void printList(List<?> list) {
        for (Object element : list) {
            System.out.println(element);
        }
    }

    public static double sumNumbers(List<? extends Number> numbers) {
        double sum = 0.0;
        for (Number num : numbers) {
            sum += num.doubleValue();
        }
        return sum;
    }
}
```

This example:

- Uses `ArrayList` and `HashSet` with generics to ensure type safety.
- Uses a wildcard in `printList` to accept a list of any type.
- Uses an upper-bounded wildcard in `sumNumbers` to work with any subclass of `Number`.
---
