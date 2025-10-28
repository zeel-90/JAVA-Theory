# 🔐 **Access Control in Java**

> Java’s **access control system** defines *where* and *how* class members (fields and methods) can be accessed.
> It provides **encapsulation**, protecting internal implementation details from external interference.

---

## 🧱 **The Four Access Levels**

Java provides **four levels** of access control:

| Modifier                  | Class | Package | Subclass (same pkg) | Subclass (diff pkg) | World (outside pkg) |
| ------------------------- | ----- | ------- | ------------------- | ------------------- | ------------------- |
| `public`                  | ✅     | ✅       | ✅                   | ✅                   | ✅                   |
| `protected`               | ✅     | ✅       | ✅                   | ✅                   | ❌                   |
| *(default)* (no modifier) | ✅     | ✅       | ✅                   | ❌                   | ❌                   |
| `private`                 | ✅     | ❌       | ❌                   | ❌                   | ❌                   |

✅ = Accessible
❌ = Not Accessible

---

## 🧠 **Default (Package-Private) Access**

If no modifier is specified:

* The member is **accessible only within the same package**.
* It is not accessible from outside the package.

Example:

```java
class Example {
    int data = 10; // default access
}
```

📦 Can be used freely by other classes in the same package, but not outside it.

---

## 🧩 **Protected Access**

The `protected` modifier:

* Allows access **within the same package**, and
* By **subclasses**, even if they are in **different packages**.

Example:

```java
// packageOne/Base.java
package packageOne;

public class Base {
    protected void display() {
        System.out.println("in Base");
    }
}
```

```java
// packageTwo/Derived.java
package packageTwo;
import packageOne.Base;

public class Derived extends Base {
    public void show() {
        // new Base().display(); // ❌ Not allowed
        new Derived().display(); // ✅ Allowed
        display();               // ✅ Allowed
    }
}
```

✅ **Explanation:**

* `display()` is accessible through a `Derived` instance, not through a `Base` object.
* The caller must be a **subclass instance** to access protected members outside the package.

---

## ⚙️ **Protected Access Logic**

🧩 **Rule Summary:**

> A subclass can access a protected member only through references of its **own type** or subclass type.

Example:

```java
class C {
    protected int value;
}

// In another package
class S extends C {
    void test() {
        C c = new C();
        // c.value; ❌ Not allowed — reference is of superclass type
        S s = new S();
        s.value = 5; // ✅ Allowed — reference is subclass type
    }
}
```

📘 **Why this rule?**
To ensure **safe encapsulation** — subclasses can access inherited behavior,
but not manipulate internal state of unrelated subclasses.

---

## 🔒 **Private Access**

* Members declared `private` are accessible **only within the same class**.
* Not visible to subclasses or other classes in the same package.

Example:

```java
class Secret {
    private String code = "XYZ123";

    private void reveal() {
        System.out.println(code);
    }
}
```

➡️ Only code inside `Secret` can use `code` or call `reveal()`.

---

## 🌎 **Public Access**

`public` members are visible everywhere — inside the same class, same package, subclasses, and external code.

Example:

```java
public class Student {
    public String name;
    public void greet() {
        System.out.println("Hello, " + name);
    }
}
```

✅ Can be accessed from any other class:

```java
Student s = new Student();
s.name = "Rahul";
s.greet();
```

---

## 🧩 **Understanding Access in Inheritance**

Let’s break down this snippet:

```java
package packageOne;
public class Base {
    protected void display() {
        System.out.println("in Base");
    }
}

package packageTwo;
import packageOne.Base;

public class Derived extends Base {
    public void show() {
        new Derived().display(); // ✅ Works
        display();               // ✅ Works
        // new Base().display(); // ❌ Error
    }
}
```

💡 **Explanation:**

* `Derived` is a subclass of `Base`, so it inherits the protected `display()` method.
* However, it cannot call `display()` using a `Base` object,
  only via `this` or a `Derived` instance.

---

## ⚖️ **Access Modifier Decision Guide**

| Use Case                                                 | Modifier    |
| -------------------------------------------------------- | ----------- |
| For members visible everywhere                           | `public`    |
| For members visible to subclasses and within the package | `protected` |
| For internal package-only usage                          | *(default)* |
| For complete encapsulation                               | `private`   |

---

## 🧭 **Summary / Key Takeaways**

| Concept                | Description                                              |
| ---------------------- | -------------------------------------------------------- |
| **public**             | Visible everywhere                                       |
| **protected**          | Visible in package + subclasses                          |
| **default**            | Visible only in the same package                         |
| **private**            | Visible only inside the class                            |
| **Subclass rule**      | Can access protected members only via subclass reference |
| **Encapsulation goal** | Protect internal implementation and maintain code safety |

---

💡 **Pro Tip:**
Use **private** for maximum safety, **protected** for inheritance flexibility, and **public** only when truly necessary.
Good access control keeps your code **modular, maintainable, and secure.**

---

✨ *End of Notes — Access Control in Java explained clearly and colorfully!*
