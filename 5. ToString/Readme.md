# Java `toString()` Method

## What is `toString()` in Java?

* `toString()` is a **built-in method** of the `Object` class in Java.
* It returns a **String representation** of an object.
* This method is **automatically invoked** when:

  * You pass an object to `System.out.print()` or `System.out.println()`
  * You concatenate an object with a String

### Default Behavior

* The default implementation of `toString()` returns:

  ```
  ClassName@HashCode
  ```
* This is usually **not human-readable** and not helpful for debugging.

---

## Why Override `toString()`?

* To return a **meaningful description** of an object
* Makes logs and debugging **easier**
* Improves **readability** of printed objects

Example use cases:

* Printing user details
* Logging objects
* Debugging complex data structures

---

## Example Without Overriding `toString()`

### `Cat` Class

```java
package com.amigoscode;

public class Cat {
    private String name;
    private int age;
    private String color;

    public Cat(String name, int age, String color) {
        this(name, age);
        this.color = color;
    }

    public Cat(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public Cat(String name) {
        this.name = name;
        this.age = 0;
    }

    public Cat() {}

    public void meow() {
        System.out.println(name + ": meow...");
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }
}
```

### `Main` Class

```java
package com.amigoscode;

public class Main {
    public static void main(String[] args) {
        Cat rose = new Cat("Rose", 2, "Blue");
        System.out.println(rose);

        Cat star = new Cat();
        System.out.println(star);

        Cat jupiter = new Cat("Jupiter");
        System.out.println(jupiter);
    }
}
```

### Output (Default `toString()`)

```
com.amigoscode.Cat@279f2327
com.amigoscode.Cat@2ff4acd0
com.amigoscode.Cat@54bedef2
```

### Problem with This Output

* Does **not show object data**
* Hard to understand which object contains what values

---

## Overriding the `toString()` Method

We override `toString()` to return meaningful information about the `Cat` object.

### Updated `Cat` Class with `toString()`

```java
package com.amigoscode;

public class Cat {
    private String name;
    private int age;
    private String color;

    public Cat(String name, int age, String color) {
        this(name, age);
        this.color = color;
    }

    public Cat(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public Cat(String name) {
        this.name = name;
        this.age = 0;
    }

    public Cat() {}

    public void meow() {
        System.out.println(name + ": meow...");
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }

    @Override
    public String toString() {
        return "Name: " + name +
               " Color: " + color +
               " Age:" + age;
    }
}
```

---

## Output After Overriding `toString()`

```
Name: Rose Color: Blue Age:2
Name: null Color: null Age:0
Name: Jupiter Color: null Age:0
```

### Explanation

* Now Java prints the **actual state** of the object
* `null` values indicate fields that were never initialized
* Output is **clean, readable, and useful**

---

## Key Points to Remember

* `toString()` belongs to `java.lang.Object`
* It is called **implicitly** when printing objects
* Always use `@Override` annotation
* Avoid complex logic inside `toString()`
* Very useful for **debugging and logging**

---

## Best Practice Example

```java
@Override
public String toString() {
    return String.format(
        "Cat{name='%s', age=%d, color='%s'}",
        name, age, color
    );
}
```

This format is commonly used in **production-grade Java applications**.

---
