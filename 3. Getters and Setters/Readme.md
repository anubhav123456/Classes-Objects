# Getter and Setter in Java

## What are Getters and Setters?

* **Getters and setters** are Java methods that provide controlled access to the fields (variables) of a class.
* A **getter** method is used to **read** (get) the value of a private field.
* A **setter** method is used to **modify** (set) the value of a private field.
* They support **encapsulation**, one of the core principles of Object-Oriented Programming (OOP).

---

## Why Use Getters and Setters?

1. **Encapsulation**

   * Fields are kept `private` and are not directly accessible from outside the class.

2. **Data Protection**

   * External classes cannot change fields directly.

3. **Validation**

   * Setter methods can validate data before assigning it to fields.

4. **Maintainability**

   * Internal implementation can change without affecting external code.

5. **Readability & Control**

   * Clear and controlled way to access and update object data.

---

## Getter Example

### Cat Class (Getter)

```java
package com.amigoscode;

public class Cat {
    private String name;

    public void meow() {
        System.out.println(name + ": meow...");
    }

    // getter
    public String getName() {
        return this.name;
    }
}
```

### Main Class (Using Getter)

```java
package com.amigoscode;

public class Main {
    public static void main(String[] args) {
        
        Cat rose = new Cat();
        rose.setName("Rose");
        rose.meow();
        // invoke getter method on rose
        System.out.println(rose.getName()); // Rose

        Cat star = new Cat();
        star.setName("Star");
        star.meow();
        // invoke getter method on star
        System.out.println(star.getName()); // Star

    }
}
```

**Explanation:**

* `getName()` returns the value of the private field `name`.
* The field `name` cannot be accessed directly outside the class.

---

## Setter Example

### Cat Class (Setter)

```java
package com.amigoscode;

public class Cat {
    private String name;

    public void meow() {
        System.out.println(name + ": meow...");
    }

    // setter
    public void setName(String name) {
        this.name = name;
    }
}
```

### Main Class (Using Setter)

```java
package com.amigoscode;

public class Main {
    public static void main(String[] args) {
        
        Cat rose = new Cat();
        // set rose name to Rose
        rose.setName("Rose");
        rose.meow();

        // set star name to Star
        Cat star = new Cat();
        star.setName("Star");
        star.meow();
    }
}
```

**Explanation:**

* `setName(String name)` assigns a value to the private field `name`.
* `this.name` refers to the current object's field.

---

## Getter + Setter Together (Typical Usage)

```java
public class Cat {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

---

## Key Points to Remember

* Fields should usually be **private**.
* Getters start with **get** (e.g., `getName`).
* Setters start with **set** (e.g., `setName`).
* Getters return a value; setters usually return `void`.
* Helps in **secure, clean, and maintainable** code.

---

## Interview Tip

> If a class has public fields instead of getters/setters, it breaks encapsulation and makes the code harder to maintain and secure.

---
