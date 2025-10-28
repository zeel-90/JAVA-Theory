# 🔗 **Interfaces in Java**

> Interfaces in Java define a **contract** — a promise of what a class *can do*, without specifying *how it does it.*
> They’re the solution to Java’s **lack of multiple inheritance**.

---

## 🧠 **Why Interfaces Exist**

Since Java doesn’t allow **multiple inheritance of classes**, interfaces provide a way to achieve similar flexibility.

> 🧩 Interfaces allow a class to implement *multiple behaviors* by using multiple interfaces.

---

## 🧱 **Basic Concept**

* Functions in interfaces are **abstract** and **public** by default.
* Variables are **`public static final`** (constants).
* Interfaces contain *no state*, only **behavior definitions**.

---

## ✍️ **Defining and Implementing an Interface**

```java
interface Animal {
    void sound(); // implicitly public and abstract
}

class Dog implements Animal {
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound();
    }
}
```

✅ **Output:**

```
Dog barks
```

---

## ⚡ **Interface vs Class**

| Feature     | Interface                                                                  | Class                                      |
| ----------- | -------------------------------------------------------------------------- | ------------------------------------------ |
| Contains    | Abstract methods only (till Java 7); default & static methods since Java 8 | Methods (abstract or concrete)             |
| Variables   | Always `public static final`                                               | Can have any type                          |
| Inheritance | A class can implement **multiple interfaces**                              | A class can extend **only one** superclass |
| Purpose     | Define what should be done                                                 | Define how it’s done                       |
| State       | Cannot hold state                                                          | Can maintain instance variables            |

---

## 💡 **Dynamic Method Resolution**

Interfaces support **runtime polymorphism**.
When a method is called on an interface reference, Java looks up the actual implementation **at runtime**.

This allows **flexible and extensible code** — classes can be developed later and still work with existing interface-based code.

⚠️ However, this dynamic lookup incurs a **small performance cost** in critical code.

---

## 🧩 **Nested Interfaces**

> Interfaces can be nested inside classes or even other interfaces.

```java
class A {
    public interface NestedIF {
        boolean isNotNegative(int x);
    }
}

class B implements A.NestedIF {
    public boolean isNotNegative(int x) {
        return x >= 0;
    }
}

public class NestedIFDemo {
    public static void main(String[] args) {
        A.NestedIF nif = new B();
        if (nif.isNotNegative(10))
            System.out.println("10 is not negative");
    }
}
```

✅ **Output:**

```
10 is not negative
```

📘 A nested interface can be declared as **public, private, or protected**, while top-level interfaces can only be **public** or **default**.

---

## 🧬 **Interface Inheritance**

Interfaces can **extend other interfaces** using the `extends` keyword.

```java
interface A {
    void display();
}

interface B extends A {
    void show();
}
```

Any class that implements `B` must implement **both** `display()` and `show()`.

---

## 🧱 **Default & Static Methods (Java 8+)**

> Introduced to allow interface updates without breaking existing code.

### 🧩 Default Method Example

```java
interface MyInterface {
    default String getMessage() {
        return "Default implementation";
    }
}
```

* Default methods provide **optional behavior**.
* If a class implements multiple interfaces with the same default method, the compiler throws an error unless the method is overridden.

### ⚙️ Static Interface Methods

```java
interface Utility {
    static void help() {
        System.out.println("Static method in interface");
    }
}
```

⚠️ **Static methods in interfaces:**

* Must have a body.
* Are **not inherited** by implementing classes or subinterfaces.

---

## ⚔️ **Class vs Interface Default Priority**

| Case                                            | Result                                 |
| ----------------------------------------------- | -------------------------------------- |
| Class defines method + interface default method | **Class version wins**                 |
| Two interfaces define same default method       | **Must override in class**, else error |
| One interface extends another with same default | **Child interface version wins**       |

---

## ⚠️ **Important Notes**

* Interface methods are **implicitly public** — implementing methods must also be `public`.
* A class can **implement multiple interfaces** (multi-type polymorphism).
* Interface variables are **constants** (final + static).
* Interfaces help **decouple code**, improving modularity and scalability.

---

## 🧭 **Summary / Key Takeaways**

| Concept                 | Description                                            |
| ----------------------- | ------------------------------------------------------ |
| **interface**           | Defines a set of abstract behaviors                    |
| **implements**          | Used by a class to implement an interface              |
| **Default method**      | Provides a base implementation (since Java 8)          |
| **Static method**       | Must have a body; not inherited                        |
| **Nested interface**    | Interface declared inside a class or another interface |
| **Dynamic dispatch**    | Method calls resolved at runtime                       |
| **Multiple interfaces** | Enables multiple inheritance-like behavior             |

---

💡 **Pro Tip:**
Use **interfaces** to define **capabilities** (like `Flyable`, `Runnable`, `Serializable`) — not to model relationships.
They make your system **pluggable, flexible, and future-proof** 🔥

---

✨ *End of Notes — Interfaces in Java made visual, simple, and powerful!*
