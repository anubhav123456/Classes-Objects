
---

# Java Constructors

## 1. What is a Constructor?

* A **constructor** is a special method used to **initialize an object**.
* It is **called automatically** when an object of a class is created.
* Constructor:

  * Has **same name as the class**
  * Has **no return type**
* If **no constructor is defined**, Java automatically provides a **default constructor**.

---

## 2. Constructor Example

### Cat class with constructor

```java
package com.amigoscode;

public class Cat {
    private String name;
    private int age;

    // Constructor
    public Cat(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void meow() {
        System.out.println(name + ": meow...");
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return this.name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

### Using the constructor

```java
package com.amigoscode;

public class Main {
    public static void main(String[] args) {
        Cat rose = new Cat("Rose", 2);
        rose.meow();
        System.out.println(rose.getName());
        System.out.println(rose.getAge());
    }
}
```

✅ The constructor initializes `name` and `age` at object creation.

---

## 3. Default Constructor

### What is a Default Constructor?

* Automatically generated **only if no constructor is defined**
* Initializes instance variables to their **default values**

  * `String → null`
  * `int → 0`

---

### Class without an explicit constructor

```java
package com.amigoscode;

public class Cat {
    private String name;
    private int age;

    public void meow() {
        System.out.println(name + ": meow...");
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return this.name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

---

### ❌ This code NO longer works

```java
package com.amigoscode;

public class Main {
    public static void main(String[] args) {
        Cat rose = new Cat("Rose", 2); // ❌ Error
        rose.meow();
        System.out.println(rose.getName());
    }
}
```

Reason:

* No constructor with `(String, int)` exists
* Only a default constructor `Cat()` is generated

---

### ✅ Correct way using default constructor

```java
package com.amigoscode;

public class Main {
    public static void main(String[] args) {
        Cat star = new Cat();
        star.setName("Star");
        star.meow();
        System.out.println(star.getName());
    }
}
```

---

## 4. Adding Constructor Back

```java
public Cat(String name, int age) {
    this.name = name;
    this.age = age;
}
```

Now you can create objects using:

```java
Cat rose = new Cat("Rose", 2);
Cat rose = new Cat();
```

---

## 5. Multiple Constructors

### What are Multiple Constructors?

* A class can have **more than one constructor**
* Used to initialize objects in **different ways**
* This is called **constructor overloading**

---

### Cat class with 3 constructors

```java
package com.amigoscode;

public class Cat {
    private String name;
    private int age;

    public Cat(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public Cat(String name) {
        this.name = name;
        this.age = -1;
    }

    public Cat() {}

    public void meow() {
        System.out.println(name + ": meow...");
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return this.name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

---

### Using all 3 constructors

```java
package com.amigoscode;

public class Main {
    public static void main(String[] args) {

        Cat rose = new Cat("Rose", 2);
        rose.meow();
        System.out.println(rose.getName());
        System.out.println(rose.getAge());

        System.out.println();

        Cat star = new Cat();
        star.setName("Star");
        star.meow();
        System.out.println(star.getName());

        Cat jupiter = new Cat("Jupiter");
        System.out.println(jupiter.getName());
        System.out.println(jupiter.getAge());
    }
}
```

---

## 6. The `this` Keyword

### Purpose of `this`

* Refers to the **current object**
* Used to differentiate **instance variables** from **local variables**

---

### Example using `this`

```java
public class MyClass {
  private int myInt;

  public MyClass(int myInt) {
    this.myInt = myInt;
  }
}
```

Without `this`, Java cannot distinguish between:

* instance variable `myInt`
* constructor parameter `myInt`

---

## 7. Calling One Constructor from Another (`this()`)

* `this()` is used to call another constructor in the **same class**
* Must be the **first statement** inside the constructor

---

### Constructor chaining example

```java
public class MyClass {

  public MyClass() {
    this(10);
  }

  public MyClass(int myInt) {
    System.out.println("myInt = " + myInt);
  }

  public static void main(String[] args) {
    new MyClass();
  }
}
```

### Output

```
myInt = 10
```

---

## 8. Key Rules Summary

* Constructor name = Class name
* No return type
* Default constructor exists **only if no constructor is defined**
* Multiple constructors allowed (overloading)
* `this.variable` → instance variable
* `this()` → calls another constructor
* `this()` must be the **first line**

---
