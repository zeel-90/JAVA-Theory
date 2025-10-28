# 🧩 **Constructors, `this`, `final`, and `finalize()` in Java**

> These four concepts define **object initialization, immutability, and cleanup behavior** in Java.
> They are fundamental for understanding how Java manages **object lifecycle** and **data consistency**.

---

## 🏗️ **Constructors**

> A **constructor** is a special method that runs automatically when an object is created.

### 🔹 Characteristics:

* Has the **same name** as the class.
* **No return type** (not even `void`).
* Called **automatically** by the `new` operator.
* Used to **initialize objects**.

```java
class Box {
    Box() {
        System.out.println("Constructor called!");
    }
}

public class Main {
    public static void main(String[] args) {
        Box mybox = new Box(); // Constructor runs here
    }
}
```

✅ **Output:**

```
Constructor called!
```

---

### ⚙️ **How `new` Works**

```java
Box mybox1 = new Box();
```

`new Box()` calls the `Box()` constructor before the reference is assigned to `mybox1`.

---

### 🔁 **Default and Parameterized Constructors**

If no constructor is defined, Java automatically provides a **default constructor**.

```java
class Car {
    Car() {
        System.out.println("Default constructor called");
    }

    Car(String model) {
        System.out.println("Parameterized constructor: " + model);
    }
}
```

---

## 🧬 **Inheritance and Constructors**

> When a subclass object is created, the **superclass constructor** is always called first.

### 🔸 Example:

```java
class Base {
    Base() {
        System.out.println("Base Class Constructor Called");
    }
}

class Derived extends Base {
    Derived() {
        System.out.println("Derived Class Constructor Called");
    }
}

public class Main {
    public static void main(String[] args) {
        Derived d = new Derived();
    }
}
```

✅ **Output:**

```
Base Class Constructor Called
Derived Class Constructor Called
```

📘 **Why?**
Java ensures superclass parts of the object are initialized **before** subclass parts.

---

### ⚠️ **Parameterized Constructors and `super()`**

If the superclass doesn’t have a **default constructor**, the subclass must **explicitly call** the superclass constructor using `super()`.

```java
class Parent {
    Parent(int x) {
        System.out.println("Parent constructor " + x);
    }
}

class Child extends Parent {
    Child() {
        super(10); // must call explicitly
        System.out.println("Child constructor");
    }
}
```

---

## 🧭 **The `this` Keyword**

> `this` is a **reference** to the current object.

### 🔹 Common Uses:

1. To **refer to instance variables** when they are shadowed by parameters.
2. To **call another constructor** in the same class.
3. To **pass the current object** as an argument.

```java
class Student {
    String name;
    Student(String name) {
        this.name = name; // refers to instance variable
    }
}
```

---

### 🧩 **Using `this()` for Constructor Chaining**

```java
class Rectangle {
    int width, height;

    Rectangle() {
        this(10, 20); // calls parameterized constructor
    }

    Rectangle(int w, int h) {
        width = w;
        height = h;
    }
}
```

💡 `this()` must be the **first statement** in a constructor.

---

## 🧱 **The `final` Keyword**

> Declaring a field as `final` makes it a **constant** — its value cannot change after initialization.

```java
final int FILE_OPEN = 2;
```

### ⚙️ **Behavior:**

* For **primitive types** → value cannot change.
* For **reference types** → reference cannot change, but the object it points to *can*.

```java
final StringBuilder sb = new StringBuilder("Hello");
sb.append(" World"); // ✅ allowed
// sb = new StringBuilder("Hi"); ❌ not allowed
```

🧠 **Naming Convention:**
Use **ALL_CAPS** for constants, e.g. `MAX_SIZE`.

---

## ⚰️ **The `finalize()` Method**

> The `finalize()` method defines actions that occur **before an object is destroyed** by the garbage collector.

```java
class Resource {
    protected void finalize() {
        System.out.println("Object is being garbage collected");
    }
}
```

🧩 Java automatically calls `finalize()` before reclaiming an object’s memory.

⚠️ **Important:**

* `finalize()` is **deprecated** in modern Java (use `try-with-resources` or explicit cleanup).
* It’s **not guaranteed** to run immediately or at all.

---

## 🧭 **Summary / Key Takeaways**

| Concept                 | Description                                    |
| ----------------------- | ---------------------------------------------- |
| **Constructor**         | Special method to initialize objects           |
| **Default Constructor** | Auto-provided if none exists                   |
| **Inheritance Rule**    | Superclass constructor always runs first       |
| **`this` keyword**      | Refers to current object                       |
| **`this()`**            | Calls another constructor in same class        |
| **`final`**             | Prevents variable reassignment or modification |
| **`finalize()`**        | Cleanup before object destruction (deprecated) |

---

💡 **Pro Tip:**
Use `final` for **constants**, `this` for **clarity**, and constructors for **reliable initialization**.
Avoid `finalize()` — modern Java prefers explicit resource management.

---

✨ *End of Notes — Constructors, this, final, and finalize explained clearly and colorfully!*
