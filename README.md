# 🌟 **Java Core Concepts — Quick Reference & Guide**

> 💡 This collection of Markdown notes covers **essential Java fundamentals**,
> presented in a **modern, colorful, and easy-to-understand** way — perfect for revision, interviews, or project prep.

---

## 🧱 **1. Classes and Objects**

* A **class** is a *blueprint*; an **object** is an *instance* of that blueprint.
* Objects have **state**, **behavior**, and **identity**.
* `new` allocates memory dynamically, and the `.` operator accesses members.

🔹 Example:

```java
Box b = new Box();
b.width = 10;
```

> 🧠 Think of a class as a cookie cutter 🍪 and objects as cookies!

---

## 🏗️ **2. Constructors, `this`, `final`, and `finalize()`**

* **Constructors** initialize objects automatically when `new` is called.
* **`this`** → refers to the current object.
* **`final`** → makes variables constants or prevents overriding.
* **`finalize()`** → runs before garbage collection (deprecated ⚠️).

🔹 Example:

```java
class Student {
    final String name;
    Student(String name) { this.name = name; }
}
```

> ✨ Always use constructors for clean initialization — avoid `finalize()` in modern Java.

---

## ⚙️ **3. Static Keyword**

* `static` means **shared across all instances**.
* Can apply to **variables, methods, blocks**, and **nested classes**.
* `main()` is static so JVM can run it without creating an object.

🔹 Example:

```java
static int counter = 0;
static void showCount() { System.out.println(counter); }
```

> ⚡ Perfect for utilities, constants, and counters.

---

## 🔐 **4. Access Control**

| Modifier    | Same Class | Package | Subclass | World |
| ----------- | ---------- | ------- | -------- | ----- |
| `private`   | ✅          | ❌       | ❌        | ❌     |
| *(default)* | ✅          | ✅       | ❌        | ❌     |
| `protected` | ✅          | ✅       | ✅        | ❌     |
| `public`    | ✅          | ✅       | ✅        | ✅     |

> 🧠 Use `private` for data safety, `protected` for inheritance, and `public` for APIs.

---

## 🔁 **5. Method Overloading**

* **Same method name**, different parameters (type, number, or order).
* Achieves **compile-time polymorphism**.

🔹 Example:

```java
void show(int a); 
void show(String s);
```

> 💬 Used in `System.out.println()` — Java decides which version to call at compile-time.

---

## 🔄 **6. Method Overriding**

* A **subclass redefines** a method from its superclass.
* Enables **runtime polymorphism** via **dynamic dispatch**.

🔹 Example:

```java
class Dog extends Animal {
    @Override void sound() { System.out.println("Bark!"); }
}
```

> 🧩 Object type (not reference type) decides which method runs at runtime.

---

## 🧬 **7. Inheritance**

* Enables **code reuse** and **hierarchical relationships**.
* The `extends` keyword connects child and parent classes.
* Supports **method overriding** and **constructor chaining**.

🔹 Example:

```java
class Car extends Vehicle { }
```

> 🚗 Real-world example: `Vehicle → Car → ElectricCar`.

---

## 🧠 **8. Abstract Classes and Interfaces**

* **Abstract Class**: Can have both implemented and abstract methods.
* **Interface**: Defines **pure abstraction** (no implementation).

🔹 Example:

```java
interface Shape { void draw(); }
abstract class Polygon implements Shape { abstract void sides(); }
```

> 🧩 Interfaces define *what* to do; abstract classes define *how to start*.

---

## 📦 **9. Packages**

* Organize code into **namespaces**.
* Prevent naming conflicts and enhance modularity.

🔹 Example:

```java
package shapes;
import java.util.Scanner;
```

> 📁 Think of packages as folders for your code files.

---

## 🎨 **10. Enums**

* Define **fixed sets of constants** safely and cleanly.
* Each value is a static final object.
* Can include **constructors**, **methods**, and **fields**.

🔹 Example:

```java
enum Day { MON, TUE, WED }
```

> 🌈 Ideal for representing days, directions, or status codes.

---

## 🧭 **Summary Table**

| Concept                  | Key Idea                      | Type        |
| ------------------------ | ----------------------------- | ----------- |
| **Class & Object**       | Blueprint and instance        | Core        |
| **Constructor**          | Object initialization         | Lifecycle   |
| **this / final**         | Self-reference & immutability | Control     |
| **static**               | Shared members                | Memory Mgmt |
| **Access Modifiers**     | Visibility control            | Security    |
| **Overloading**          | Compile-time polymorphism     | Syntax      |
| **Overriding**           | Runtime polymorphism          | OOP         |
| **Inheritance**          | Code reuse                    | Structure   |
| **Interface / Abstract** | Abstraction                   | Design      |
| **Enum**                 | Named constants               | Safety      |

---

## 🚀 **Final Thoughts**

> ✨ Master these 10 Java foundations and you’ll confidently handle **object-oriented design, clean code practices, and interview challenges**.
> Each topic builds the next — together they form the **backbone of Java development**.

---

💡 **Pro Tip:**
Revisit this guide before coding sessions — it’s your *Java essentials in one place!*
And yes... keep learning, keep building! 💻🔥

---

📘 *Created with ❤️ for learners who love clarity and color.*
