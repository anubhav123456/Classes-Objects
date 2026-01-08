
---

## Objects in Java

### What is an Object?

* Java is **object-oriented**, which means everything in Java is represented as an **object**.
* An **object** is a real-world entity that:

  * Has **state** → represented by variables (fields)
  * Has **behavior** → represented by methods

---

### Classes and Objects

* A **class** is a **blueprint/template**.
* An **object** is an **instance** of a class.
* The class defines:

  * What data the object will store (state)
  * What actions the object can perform (behavior)

---

### Instantiation

* Creating an object from a class is called **instantiating** the class.
* This is done using the `new` keyword.
* Once instantiated, the object can:

  * Access variables
  * Call methods defined in the class

---

### Objects in a Java Program

* A Java program can be thought of as:

  * A **collection of objects**
  * Objects **interact with each other** to perform tasks
* Objects are the **core building blocks** of Java programs.

---

### Why Objects are Important

* Objects help in:

  * Organizing code
  * Reusability
  * Maintainability
* Understanding objects is **essential** to becoming a good Java developer.

---

## Object Example in Java

### Code Example

```java
package com.amigoscode;

public class Main {
    public static void main(String[] args) {
        Cat rose = new Cat(); // <- the object called rose
        rose.name = "Rose";
        rose.meow();
    }

    // the blueprint
    static class Cat {
        private String name;
        public void meow() {
            System.out.println(name + ": meow...");
        }
    }
}
```

---

### Explanation of the Code

* `Cat` is a **class** (blueprint).
* `rose` is an **object** of the `Cat` class.
* `new Cat()` → instantiates the class.
* `name` is the **state** of the object.
* `meow()` is the **behavior** of the object.
* The object `rose`:

  * Stores data (`name`)
  * Performs actions (`meow()`)

---

### Key Takeaways

* **Class → blueprint**
* **Object → instance of a class**
* Objects have:

  * **State (variables)**
  * **Behavior (methods)**
* Objects are the **heart of Java programming**

---
