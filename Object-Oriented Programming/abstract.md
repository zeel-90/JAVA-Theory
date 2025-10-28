# 🧩 **Abstract Classes in Java**

> Abstract classes provide a **blueprint** for other classes.
> They define *what should be done*, but **not necessarily how** — leaving implementation to subclasses.

---

## 🧠 **Concept Overview**

Sometimes, you want to create a superclass that only defines **generalized behavior** for all its subclasses, while leaving the *specific details* to them.

🧱 Such a superclass is declared **abstract**.

---

## ✍️ **Declaring Abstract Methods**

```java
abstract returnType methodName(parameter-list);
```

➡️ These are *“subclass’s responsibilities”* — they must be overridden in derived classes.
➡️ Abstract methods have **no implementation** (no body).

---

## 🧩 **Declaring an Abstract Class**

Any class containing one or more abstract methods **must also** be declared abstract.

```java
abstract class Shape {
    abstract void draw();
}
```

A subclass must override `draw()` to provide meaning.

---

## 🚫 **Key Rules**

* ❌ You **cannot create objects** of an abstract class.
* ❌ Abstract constructors and abstract static methods are **not allowed**.
* ✅ You **can** have static methods inside an abstract class.
* ✅ Abstract classes **can** contain both **abstract and concrete methods**.

---

### ⚡ Example:

```java
abstract class Animal {
    abstract void sound(); // must be overridden

    void eat() {           // concrete method
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound();
        a.eat();
    }
}
```

✅ Output:

```
Dog barks
Animal is eating
```

---

## 🧩 **Why Constructors Exist in Abstract Classes**

Even though you can’t instantiate an abstract class directly, it **can have constructors** — these are used when subclasses are instantiated.

📌 For example:

```java
abstract class Base {
    Base() {
        System.out.println("Base constructor called");
    }
}

class Derived extends Base {
    Derived() {
        System.out.println("Derived constructor called");
    }
}
```

When you create a `Derived` object, the **Base constructor runs first**.

---

## 🔍 **Abstract Classes vs Interfaces**

| Feature              | Abstract Class                                              | Interface                                                        |
| -------------------- | ----------------------------------------------------------- | ---------------------------------------------------------------- |
| **Methods**          | Can have both abstract and concrete methods                 | Abstract only (till Java 7); can have default & static (Java 8+) |
| **Variables**        | Can have final, non-final, static, and non-static variables | All variables are implicitly `public static final`               |
| **Implementation**   | Can implement interfaces                                    | Cannot extend abstract classes                                   |
| **Inheritance**      | Can extend one class and implement multiple interfaces      | Can extend multiple interfaces                                   |
| **Access Modifiers** | Can have private, protected, or public members              | Members are always public                                        |
| **Object Creation**  | Cannot instantiate directly                                 | Cannot instantiate directly                                      |

---

## ⚙️ **Usage in Polymorphism**

Even though abstract classes can’t be instantiated, they can still be used as **reference types**.

```java
Shape s = new Circle();  // Allowed
```

This enables **runtime polymorphism** — the method that executes depends on the actual object type (`Circle`).

---

## 🚨 **Important Notes**

* 🧱 Abstract classes can **provide partial implementation**.
* 🧩 Subclasses **must** override all abstract methods, or themselves be declared abstract.
* 💡 Use abstract classes for shared logic with enforced contracts.

---

## 🧭 **Summary / Key Takeaways**

| Concept                  | Description                                                    |
| ------------------------ | -------------------------------------------------------------- |
| **abstract class**       | Defines a generalized form with or without implementation      |
| **abstract method**      | Must be overridden by subclasses                               |
| **No object creation**   | Cannot instantiate directly                                    |
| **Constructors allowed** | Used during subclass creation                                  |
| **Polymorphism**         | Enables runtime behavior control                               |
| **Interface difference** | Interface defines only “what”; abstract class can define “how” |

---

💡 **Pro Tip:**
Use **abstract classes** when you need **shared code + enforced structure**.
Use **interfaces** when you only want to enforce *behavioral contracts* without shared state.

---

✨ *End of Notes — Abstract Classes in Java Simplified and Colorful!*
