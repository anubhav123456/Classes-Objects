
---

## `toString()` Method in Java

* `toString()` is a built-in method of the `Object` class in Java.
* It returns a **string representation of an object**.
* This method is **automatically invoked** when an object is printed using `System.out.print()` or `System.out.println()`.
* The default implementation returns:

  ```
  ClassName@hashCode
  ```
* We can **override** this method to provide a more meaningful and readable representation of the object’s data.

### Example: Overriding `toString()`

```java
@Override
public String toString() {
    return "Name: " + name +
            " Color: " + color +
            " Age:" + age;
}
```

---

## `@Override` Annotation in Java

* The `@Override` annotation is used to indicate that a method is **overriding a method from a superclass**.
* It helps the compiler **verify correctness**.

### Benefits of `@Override` Annotation

* Ensures that the method signature **exactly matches** a method in the superclass.
* If no matching method exists in the superclass, the compiler will **throw an error**.
* Prevents accidental bugs caused by:

  * Misspelled method names
  * Incorrect method parameters
* Improves **code readability and maintainability** by clearly indicating overridden methods.

---

## Key Takeaways

* `toString()` is commonly overridden to display object details in a readable format.
* `@Override` acts as a **compile-time safety check**.
* Using `@Override` is a **best practice** when overriding any superclass method.

---
