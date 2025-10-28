# 🧬 **Inheritance in Java**

> Inheritance allows one class to **acquire the properties and methods** of another.
> It’s one of the **four core OOP principles** — used to promote *reusability, organization,* and *polymorphism.*

---

## 🏗️ **Basic Syntax**

```java
class SubclassName extends SuperclassName {
    // body of class
}
```

🔹 You can only specify **one superclass** per subclass.
🔹 Java does **not support multiple inheritance** of classes.
🔹 You can, however, create an **inheritance hierarchy** where a subclass becomes a superclass for another subclass.
🔹 A class **cannot be its own superclass.**

---

## 🔐 **Access to Members**

Although a subclass includes all members of its superclass, it **cannot access private members** directly.

---

## 🔄 **Superclass Variable Referencing Subclass Object**

> A superclass variable can reference an object of its subclass.

```java
SuperClass ref = new SubClass();
```

🧠 **Key Point:**
It’s the **type of the reference variable**, not the object type, that determines what members are accessible.

Example:

```java
plainbox = weightbox;   // (superclass = subclass)
```

Here, `plainbox` can access only members defined in `Box`, even though it actually refers to a `BoxWeight` object.

---

## 🪜 **Using `super` Keyword**

### 1️⃣ **Calling Superclass Constructor**

Whenever a subclass needs to refer to its immediate superclass, it can do so using the `super` keyword.

```java
class BoxWeight extends Box {
    double weight;

    BoxWeight(double w, double h, double d, double m) {
        super(w, h, d); // call superclass constructor
        weight = m;
    }
}
```

🧩 This allows the superclass (`Box`) to handle its own initialization (like width, height, depth), while the subclass (`BoxWeight`) handles only its specific members.

> 🧠 `super()` always refers to the **immediate superclass constructor**, even in multi-level hierarchies.

---

### 2️⃣ **Accessing Hidden Members or Methods**

You can use `super` to access a superclass member that’s hidden by a subclass member.

```java
super.member;
```

`member` can be either a method or an instance variable.

---

## 🧰 **Constructor Execution Order**

> Constructors run **from top (superclass) to bottom (subclass)** in the inheritance chain.

If the superclass constructor requires parameters, all subclasses must pass those parameters **“up the line.”**

If `super()` is *not* used, the compiler automatically calls the **default (no-arg) constructor** of the superclass.

---

## 🧱 **Using `final` with Inheritance**

The `final` keyword has three main uses 👇

---

### 🔸 1. **Create Named Constants**

`final` can mark variables that should never change.

---

### 🔸 2. **Prevent Method Overriding**

To disallow a method from being overridden:

```java
final void display() {
    System.out.println("Cannot be overridden");
}
```

✅ **Performance Boost:**
Since `final` methods can’t be overridden, the compiler can **inline** their calls for faster execution.

* 🕐 Overridable methods → *Late Binding (runtime)*
* ⚡ Final methods → *Early Binding (compile-time)*

---

### 🔸 3. **Prevent Inheritance**

To make a class non-inheritable:

```java
final class SecureData { }
```

Declaring a class `final` implicitly makes all its methods `final`.
🚫 You **cannot declare a class as both `abstract` and `final`**.

---

## ⚙️ **Static Methods and Inheritance**

* Static methods can be **inherited** but **not overridden**.
* They are **resolved at compile time** (not runtime).
* Therefore, **polymorphism does not apply** to static methods.

> 🔸 Static interface methods are **not inherited** and must always have a **body**.

---

## 🧩 **Polymorphism Limitation**

Polymorphism applies to **methods**, not to **instance variables**.

> Even if a subclass redefines a variable with the same name,
> the reference type (not the object type) decides which variable is accessed.

---

## 🧭 **Summary / Key Takeaways**

| Concept            | Description                           |
| ------------------ | ------------------------------------- |
| **extends**        | Used to inherit from a superclass     |
| **super()**        | Calls the superclass constructor      |
| **super.member**   | Accesses hidden members of superclass |
| **final method**   | Cannot be overridden                  |
| **final class**    | Cannot be inherited                   |
| **Static methods** | Inherited but not overridden          |
| **Polymorphism**   | Works only on methods, not variables  |

---

💡 **Pro Tip:**
Use inheritance for *“is-a”* relationships (e.g., `Dog extends Animal`).
For *“has-a”* relationships (e.g., `Car has Engine`), use **composition** instead.

---

✨ *End of Notes — Inheritance in Java made simple and visual!*
