# 🔁 **Method Overriding in Java**

> **Method Overriding** allows a subclass to **redefine** a method that already exists in its superclass — enabling **runtime polymorphism**.
> It’s one of the most powerful features of **Object-Oriented Programming (OOP)** in Java.

---

## 🧩 **Definition**

When a subclass defines a method with the **same name and type signature** as a method in its superclass,
the subclass version **overrides** the superclass version.

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Test {
    public static void main(String[] args) {
        Animal obj = new Dog();
        obj.sound();
    }
}
```

✅ **Output:**

```
Dog barks
```

🧠 **Explanation:**
Even though the reference is of type `Animal`, the `Dog` version of `sound()` runs —
because the actual **object type** decides the behavior at runtime.

---

## ⚙️ **Rules for Overriding**

| Rule                                 | Description                                    |
| ------------------------------------ | ---------------------------------------------- |
| ✅ Same method name                   | Must match exactly                             |
| ✅ Same parameter list                | Must have identical parameters                 |
| ⚠️ Same or compatible return type    | Covariant return types allowed (subclass type) |
| ✅ Access modifier                    | Can be same or *more accessible*               |
| 🚫 Static, final, or private methods | Cannot be overridden                           |
| ✅ Must involve inheritance           | Parent → Child relationship required           |

---

## 🧬 **Dynamic Method Dispatch**

> The mechanism that enables **runtime resolution** of overridden methods.

🧩 **How it works:**

* A superclass reference variable can refer to a subclass object.
* When a method is called, Java decides **which version** to execute **at runtime**, based on the actual object type.

```java
Animal a = new Dog(); // superclass ref → subclass object
a.sound(); // Calls Dog’s sound()
```

⚙️ **Why it matters:**
This allows **runtime polymorphism** — behavior changes dynamically depending on the object instance.

---

## 🔄 **Overriding with Covariant Return Types**

Java allows the **return type** of the overriding method to be a **subtype** of the original return type.

```java
class A {
    A get() { return this; }
}

class B extends A {
    @Override
    B get() { return this; }  // covariant return type
}
```

✅ **Explanation:**
The overridden `get()` in `B` returns a more specific type (`B` instead of `A`).

---

## ⚔️ **Overriding vs Overloading**

| Feature                  | Overriding                        | Overloading                                |
| ------------------------ | --------------------------------- | ------------------------------------------ |
| **Definition**           | Redefining a method in a subclass | Same method name with different parameters |
| **Polymorphism Type**    | Runtime polymorphism              | Compile-time polymorphism                  |
| **Inheritance Required** | Yes                               | No                                         |
| **Return Type**          | Same or covariant                 | Can differ (if parameter list changes)     |
| **Access Modifier**      | Same or more accessible           | Any                                        |
| **Static Binding?**      | Late (runtime)                    | Early (compile-time)                       |

---

## ⚠️ **Important Notes**

* You can’t override:

  * `static` methods (they are class-level, not instance-level)
  * `final` methods (they’re locked)
  * `private` methods (they’re not inherited)

* You *can* hide static methods (known as **method hiding**), but it’s not true overriding.

---

## 🧠 **Example: Dynamic Dispatch in Action**

```java
class A {
    void callme() {
        System.out.println("Inside A’s callme");
    }
}

class B extends A {
    void callme() {
        System.out.println("Inside B’s callme");
    }
}

class C extends A {
    void callme() {
        System.out.println("Inside C’s callme");
    }
}

public class DispatchDemo {
    public static void main(String[] args) {
        A a; // reference of type A

        a = new B();
        a.callme(); // Inside B’s callme

        a = new C();
        a.callme(); // Inside C’s callme
    }
}
```

✅ **Output:**

```
Inside B’s callme
Inside C’s callme
```

📘 **Explanation:**
The same reference variable `a` behaves differently depending on the object it refers to — this is **polymorphism in action**.

---

## 🧭 **Summary / Key Takeaways**

| Concept                   | Description                                   |
| ------------------------- | --------------------------------------------- |
| **Overriding**            | Redefining inherited methods in a subclass    |
| **Dynamic Dispatch**      | Runtime resolution of which method to run     |
| **Covariant Return Type** | Overridden method can return a subclass type  |
| **Cannot Override**       | Static, final, or private methods             |
| **Inheritance Required**  | Must involve parent and child class           |
| **Runtime Polymorphism**  | Behavior decided at runtime, not compile-time |

---

💡 **Pro Tip:**
Use method overriding to implement **customized subclass behavior** while keeping a **consistent API** —
It’s what makes polymorphism powerful and flexible in frameworks like Spring, Android, and JavaFX.

---

✨ *End of Notes — Method Overriding in Java made clear and colorful!*
