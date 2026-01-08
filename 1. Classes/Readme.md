
---

# Java Class – Notes

## 1. What is a Class in Java?

* A **class** in Java is a **blueprint** for creating objects.
* It defines:

  * **Variables (properties/fields)**
  * **Methods (behaviors/functions)**
* Any object created from a class will have the **same structure** (variables and methods).

### Uses of Classes

* Represent **real-world objects** (Car, Animal, Cat)
* Represent **abstract concepts** (Point, Complex Number)

### Important Points

* Every Java program must have **at least one class**.
* The **`main` method** is the entry point of a Java program.
* Classes can:

  * Be **public** (accessible everywhere)
  * Be **private** (accessible only within the defining class)
* Classes support **inheritance**:

  * A child class automatically gets all variables and methods of the parent class.
  * Promotes **code reuse** and avoids duplication.

---

## 2. Example: Cat Class

```java
static class Cat {
    // properties
    private String name;

    // behaviors
    public void meow() {
        System.out.println(name + ": meow...");
    }
}
```

### Explanation

* `name` → private instance variable
* `meow()` → instance method
* `static class` → nested class
* Encapsulation is achieved using `private`

---

## 3. Class Members in Java

Class members can be:

1. **Variables**
2. **Methods**

Each class member can be:

* **Instance member**
* **Static (class) member**
* **Final**

---

## 4. Instance Class Members

### Definition

* Instance members:

  * Belong to an **object**
  * Require **object instantiation**
  * Are **unique per object**

---

### Example: Customer Class (Instance Members)

```java
public class Customer {
    private String firstName;
    private String lastName;

    public Customer(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    public String getLastName() {
        return lastName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }

    public String getFirstName() {
        return firstName;
    }

    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }
}
```

### Key Points

* `firstName` and `lastName` are **instance variables**
* Getters and setters are **instance methods**
* Each object stores **its own copy** of instance variables

---

### Using Instance Members

```java
public class Main {
    public static void main(String[] args) {
        Customer firstCustomer = new Customer("Arnold","Rimmer");
        Customer secondCustomer = new Customer("David","Lister");

        firstCustomer.setFirstName("Arnold J.");
        secondCustomer.setFirstName("Dave");

        System.out.println(firstCustomer.getFirstName());   // Arnold J.
        System.out.println(secondCustomer.getFirstName());  // Dave
    }
}
```

### Output

```
Arnold J.
Dave
```

### Explanation

* Two separate objects → two separate data sets
* Instance members do **not interfere** with each other

---

## 5. Static Class Members

### Definition

* Static members:

  * Belong to the **class**, not the object
  * Can be accessed **without creating an object**
  * Are **shared across all instances**

---

### Example: Customer Class with Static Member

```java
public class Customer {
    private String firstName;
    private String lastName;
    private static int numberOfPeople = 0;

    public Customer(String firstName, String lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
        numberOfPeople++;
    }

    public String getLastName() {
        return lastName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }

    public String getFirstName() {
        return firstName;
    }

    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }

    public static int getNumberOfPeople() {
        return numberOfPeople;
    }
}
```

### Key Points

* `numberOfPeople` is **static**
* Shared across all objects
* Incremented whenever a new `Customer` object is created

---

### Accessing Static Members

```java
public class Main {
    public static void main(String[] args) {
        System.out.println(Customer.getNumberOfPeople());   // 0

        Customer firstCustomer = new Customer("Arnold","Rimmer");
        Customer secondCustomer = new Customer("David","Lister");

        System.out.println(firstCustomer.getFirstName());   // Arnold
        System.out.println(secondCustomer.getFirstName());  // David

        System.out.println(firstCustomer.getNumberOfPeople());  // 2
        System.out.println(secondCustomer.getNumberOfPeople()); // 2
        System.out.println(Customer.getNumberOfPeople());       // 2
    }
}
```

### Output

```
0
Arnold
David
2
2
2
```

### Explanation

* Static data is **shared**
* Accessed via:

  * Class name (recommended)
  * Object reference (allowed but not recommended)

---

## 6. Instance vs Static (Quick Comparison)

| Feature         | Instance Member     | Static Member |
| --------------- | ------------------- | ------------- |
| Belongs to      | Object              | Class         |
| Requires object | Yes                 | No            |
| Memory          | Separate per object | Shared        |
| Access          | object.member       | Class.member  |

---
