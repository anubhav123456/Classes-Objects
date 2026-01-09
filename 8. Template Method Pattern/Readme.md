
---

# 🔹 What is the Template Method Pattern?

### **Definition**

Template Method Pattern is a **behavioral design pattern** in which:

* The **algorithm’s skeleton (overall flow)** is defined in the parent (abstract) class
* **Some steps are fixed**
* **Some steps are implemented or customized by subclasses**

👉 Meaning: **Structure remains the same, but implementation can change**

---

## 🔹 Real-Life Analogy ☕

### Making Tea vs Coffee

**Fixed Steps:**

1. Boil water
2. Add ingredients
3. Pour into a cup

**Changeable Step:**

* Tea leaves vs Coffee powder

➡️ Flow is the same, ingredients differ

---

## 🔹 When to Use the Template Method Pattern?

Use this pattern when:

* The **overall algorithm flow is the same**
* Some steps **vary for different implementations**
* You want to **avoid code duplication**
* You want to keep **framework-level control in the parent class**

---

## 🔹 Structure

```
AbstractClass
 ├── templateMethod()   <-- final
 ├── step1()            <-- common
 ├── abstract step2()   <-- implemented by subclasses
 └── hook()             <-- optional override
```

---

## 🔹 Java Example (Classic)

### 🔸 Abstract Class

```java
abstract class PaymentProcess {

    // Template Method
    public final void processPayment() {
        validateRequest();
        debitAmount();
        calculateFee();
        creditAmount();
        sendReceipt();
    }

    protected void validateRequest() {
        System.out.println("Validating payment request");
    }

    protected abstract void debitAmount();

    protected abstract void creditAmount();

    // Hook method (optional)
    protected void calculateFee() {
        // default: no fee
    }

    protected void sendReceipt() {
        System.out.println("Sending receipt");
    }
}
```

---

### 🔸 Subclass: UPI Payment

```java
class UPIPayment extends PaymentProcess {

    @Override
    protected void debitAmount() {
        System.out.println("Debiting amount via UPI");
    }

    @Override
    protected void creditAmount() {
        System.out.println("Crediting amount to merchant via UPI");
    }
}
```

---

### 🔸 Subclass: Credit Card Payment

```java
class CreditCardPayment extends PaymentProcess {

    @Override
    protected void debitAmount() {
        System.out.println("Debiting amount from credit card");
    }

    @Override
    protected void creditAmount() {
        System.out.println("Crediting amount to merchant");
    }

    @Override
    protected void calculateFee() {
        System.out.println("Calculating credit card processing fee");
    }
}
```

---

### 🔸 Client Code

```java
public class Main {
    public static void main(String[] args) {
        PaymentProcess payment = new UPIPayment();
        payment.processPayment();

        System.out.println("------");

        payment = new CreditCardPayment();
        payment.processPayment();
    }
}
```

---

## 🔹 Output (Same Flow, Different Behavior)

```
Validating payment request
Debiting amount via UPI
Crediting amount to merchant via UPI
Sending receipt
------
Validating payment request
Debiting amount from credit card
Calculating credit card processing fee
Crediting amount to merchant
Sending receipt
```

---

## 🔹 Key Interview Points 🔥

### ✅ Why is `templateMethod()` marked as `final`?

➡️ So that subclasses **cannot change the order of the algorithm steps**

---

### ✅ Template Method vs Strategy Pattern

| Template Method           | Strategy              |
| ------------------------- | --------------------- |
| Based on inheritance      | Based on composition  |
| Algorithm structure fixed | Algorithm replaceable |
| Compile-time behavior     | Runtime behavior      |

---

### ✅ Why Template Method Uses Abstract Class?

* Enables shared code reuse
* Allows partial implementation
* Centralizes control flow

---

## 🔹 Hook Method (Very Important)

A **hook method** is an optional method.
Subclasses **may override it or may ignore it**.

```java
protected boolean isLoggingEnabled() {
    return false;
}
```

---

## 🔹 Real-World Use Cases

* Spring Framework (`AbstractController`, `OncePerRequestFilter`)
* Servlet lifecycle (`service()`, `doGet()`, `doPost()`)
* JDBC (`execute()`, `executeQuery()`)
* Game engines (game loop)
* Data processing pipelines

---

## 🔹 One-Line Interview Answer 💯

> *Template Method Pattern defines the skeleton of an algorithm in a base class while allowing subclasses to override specific steps without changing the algorithm’s structure.*

---
