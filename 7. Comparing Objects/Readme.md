
---

# Comparing Objects in Java

## Why Object Comparison Matters

Comparing objects is a fundamental part of Java programming. Java provides **multiple ways** to compare objects, but choosing the wrong one can lead to bugs and unexpected behavior.

The **two main ways** to compare objects in Java are:

1. `==` operator
2. `.equals()` method

---

## 1. Using `==` to Compare Objects

### What `==` Does

* `==` is known as the **identity operator**
* It checks **whether two references point to the same object in memory**
* It does **NOT** compare object contents

### Example: Same Object Reference

```java
Object obj1 = new Object(); // obj1 is pointing to a new object in memory
Object obj2 = obj1;        // obj2 is pointing to the same object as obj1

System.out.println(obj1 == obj2); // Prints true
```

✔️ `true` because both references point to the **same memory location**

---

### Example: Different Objects

```java
Object obj1 = new Object(); // Creates a new object
Object obj2 = new Object(); // Creates another new object

System.out.println(obj1 == obj2); // Prints false
```

❌ `false` because these are **two different objects in memory**, even though they are of the same type.

---

### When to Use `==`

* Checking if two references point to the **exact same object**
* Comparing **enums**
* Performance-critical identity checks

---

## 2. Using `.equals()` to Compare Objects

### What `.equals()` Does

* Compares the **contents (values)** of two objects
* Two objects can be equal **even if they are stored in different memory locations**
* Most commonly used for object comparison

---

### Example: String Comparison

```java
String str1 = "Hello";
String str2 = new String("Hello"); // Creates separate object
String str3 = " World";

System.out.println(str1 + str3); // Prints "Hello World"
System.out.println(str1 == (str2 + str3)); // Prints false
System.out.println(str1.equals((str2 + str3))); // Prints true
```

### Explanation

* `str1` and `str2` contain the same value `"Hello"` but are stored differently
* `==` fails because references differ
* `.equals()` succeeds because **values match**

---

### Key Difference Summary

| Comparison  | Checks           | Result           |
| ----------- | ---------------- | ---------------- |
| `==`        | Memory reference | Same object only |
| `.equals()` | Object content   | Same values      |

---

## 3. `equals()` and `hashCode()` Methods

### Why They Matter

* Used heavily in **collections** like `HashMap`, `HashSet`
* Proper implementation ensures **correct object comparison**
* Both must be overridden together

---

### Important Rules

* If two objects are equal using `.equals()`, they **must** have the same `hashCode()`
* Default implementations come from `Object` class
* We override them to define **custom equality logic**

---

## 4. Overriding `equals()` Method

```java
@Override
public boolean equals(Object o) {
    if (this == o) return true;
    if (o == null || getClass() != o.getClass()) return false;

    Person person = (Person) o;

    return Objects.equals(name, person.name)
        && Objects.equals(email, person.email)
        && Objects.equals(phoneNumber, person.phoneNumber)
        && gender == person.gender;
}
```

### Explanation

* `this == o` → Same reference check (fast)
* `o == null` → Null safety
* `getClass()` → Ensures same class
* Field-by-field comparison using `Objects.equals()`

---

## 5. Overriding `hashCode()` Method

```java
@Override
public int hashCode() {
    return Objects.hash(name, email, phoneNumber, gender);
}
```

### Explanation

* Uses the same fields as `equals()`
* Ensures consistency between `equals()` and `hashCode()`

---

## 6. IDE Support

* `equals()` and `hashCode()` are **boilerplate**
* Most IDEs (IntelliJ, Eclipse) can **auto-generate** them
* Still important to understand how they work internally

---

## Final Takeaways

* Use `==` → when checking **reference equality**
* Use `.equals()` → when checking **value equality**
* Always override **both** `equals()` and `hashCode()`
* Correct comparison prevents bugs in collections and business logic

---
