# ⚙️ **The `static` Keyword in Java**

> The `static` keyword in Java allows members (variables, methods, blocks, and nested classes)
> to **belong to the class itself**, not to any specific object.
> It is used when behavior or data should be **shared across all instances**.

---

## 🧠 **Understanding Static**

When a member is declared `static`, it:

* Can be accessed **before any objects** of its class are created.
* Belongs to the **class**, not to individual objects.
* Is shared across **all instances** of the class.

```java
class Counter {
    static int count = 0;

    Counter() {
        count++;
        System.out.println(count);
    }

    public static void main(String[] args) {
        new Counter();
        new Counter();
        new Counter();
    }
}
```

✅ **Output:**

```
1
2
3
```

📘 All objects share the same `count` variable — because it’s `static`.

---

## 💡 **Why `main()` is Static**

The `main()` method is declared `static` because:

* It must run **before** any objects exist.
* The JVM calls it directly without creating an instance of the class.

```java
public static void main(String[] args) { }
```

---

## 🔧 **Static Methods**

A static method:

* Can access only **static variables**.
* Cannot access **non-static (instance)** variables directly.
* Cannot use `this` or `super`.
* Can be called using the **class name**.

Example:

```java
public class Human {
    String message = "Hello World";

    public static void display(Human human) {
        System.out.println(human.message); // Access via object reference
    }

    public static void main(String[] args) {
        Human kunal = new Human();
        kunal.message = "Kunal's message";
        Human.display(kunal); // ✅ Works
    }
}
```

📘 You can access non-static data from static context **only through an object reference**.

---

## ⚙️ **Static Blocks**

Used for complex initialization of static variables.
Runs **once**, when the class is first loaded.

```java
class UseStatic {
    static int a = 3;
    static int b;

    static void meth(int x) {
        System.out.println("x = " + x);
        System.out.println("a = " + a);
        System.out.println("b = " + b);
    }

    static {
        System.out.println("Static block initialized.");
        b = a * 4;
    }

    public static void main(String[] args) {
        meth(42);
    }
}
```

✅ **Output:**

```
Static block initialized.
x = 42
a = 3
b = 12
```

💡 **Order of Execution:**
1️⃣ Static variables → 2️⃣ Static block → 3️⃣ `main()` method

---

## 🧱 **Static Variables**

* Shared by **all instances** of a class.
* Useful for counting objects, caching data, or defining constants.

Example:

```java
class MathUtil {
    static final double PI = 3.14159;
}
```

📘 Access directly as `MathUtil.PI`.

---

## 🧩 **Static Nested Classes**

> Only **nested classes** can be declared static.

A static nested class **does not need an instance** of the outer class.

```java
public class Static {
    static class Test {
        String name;
        Test(String name) { this.name = name; }
    }

    public static void main(String[] args) {
        Test a = new Test("Kunal");
        Test b = new Test("Rahul");

        System.out.println(a.name); // Kunal
        System.out.println(b.name); // Rahul
    }
}
```

✅ `Test` does not depend on an instance of `Static`.

📘 **Explanation:**
A static nested class has **no implicit reference** to its enclosing class.

---

## 🚫 **Static Method Limitations**

| Limitation                                | Description                    |
| ----------------------------------------- | ------------------------------ |
| ❌ Cannot override static methods          | They are bound at compile-time |
| ❌ Cannot access instance members directly | Instance context doesn’t exist |
| ❌ Cannot use `this` or `super`            | No instance context            |

Static methods belong to the **class**, not the object, so overriding doesn’t make sense.
This is why **static interface methods are not inherited**.

---

## 🧬 **Static Interface Methods**

* Must have a **body**.
* Are **not inherited** by implementing classes or subinterfaces.

Example:

```java
interface Utility {
    static void print() {
        System.out.println("Static method in interface");
    }
}
```

Call it as:

```java
Utility.print(); // ✅ Allowed
```

---

## 🧭 **Summary / Key Takeaways**

| Concept                 | Description                                        |
| ----------------------- | -------------------------------------------------- |
| **Static Variable**     | Belongs to class; shared by all instances          |
| **Static Method**       | Belongs to class; can access only static data      |
| **Static Block**        | Runs once when class loads                         |
| **Static Nested Class** | Does not need instance of outer class              |
| **main()**              | Static because program starts before objects exist |
| **Cannot Override**     | Static methods are class-level, not instance-level |

---

💡 **Pro Tip:**
Use static for **utility functions**, **shared constants**, and **singleton logic**.
Avoid overusing it in OOP-heavy designs — it can reduce flexibility and testability.

---

✨ *End of Notes — Static Keyword in Java made simple and practical!*
