# 🎨 **Enums (Enumerations) in Java**

> An **enum** is a list of **named constants** — a type-safe way to represent a fixed set of values.
> Unlike C/C++, Java enums are **classes** that can have methods, constructors, and fields.

---

## 🧩 **Defining an Enum**

```java
enum Color {
    RED, BLUE, GREEN;
}
```

✅ Each constant (`RED`, `BLUE`, `GREEN`) is a **static final instance** of `Color`.

Equivalent internal representation:

```java
class Color {
    public static final Color RED = new Color();
    public static final Color BLUE = new Color();
    public static final Color GREEN = new Color();
}
```

---

## ⚙️ **Enum Characteristics**

| Feature                  | Description                                    |
| ------------------------ | ---------------------------------------------- |
| **Type-safe**            | Cannot assign arbitrary integers like in C/C++ |
| **Implicitly extends**   | `java.lang.Enum`                               |
| **Cannot extend**        | Any other class                                |
| **Can implement**        | Interfaces                                     |
| **Cannot be subclassed** | Enums are implicitly `final`                   |

---

## 💬 **Basic Enum Usage**

```java
enum Color { RED, GREEN, BLUE }

public class Test {
    public static void main(String[] args) {
        Color c = Color.RED;
        System.out.println(c);
    }
}
```

✅ **Output:**

```
RED
```

---

## ⚡ **Enum Methods**

All enums inherit from `java.lang.Enum`, which provides these useful methods:

| Method                 | Description                                |
| ---------------------- | ------------------------------------------ |
| `values()`             | Returns all enum constants                 |
| `ordinal()`            | Returns the position (index) of a constant |
| `valueOf(String name)` | Returns enum constant with the given name  |
| `toString()`           | Returns the constant’s name                |

Example:

```java
for (Color c : Color.values()) {
    System.out.println(c + " at index " + c.ordinal());
}
```

✅ **Output:**

```
RED at index 0
GREEN at index 1
BLUE at index 2
```

---

## 🧱 **Enum Constructors**

Enums can have constructors — but they are **executed once per constant**, when the enum is first loaded.

```java
enum Color {
    RED("Stop"), GREEN("Go"), BLUE("Calm");

    private String meaning;

    private Color(String meaning) {
        this.meaning = meaning;
    }

    public String getMeaning() {
        return meaning;
    }
}
```

✅ **Output:**

```
Stop
Go
Calm
```

⚠️ **Rules:**

* Enum constructors are **private or package-private**.
* You cannot call them manually (`new` is not allowed).

---

## 🧩 **Enums and Methods**

Enums can include **concrete methods** (but not abstract ones):

```java
enum Day {
    MON, TUE, WED;

    public void printDay() {
        System.out.println("Day is: " + this);
    }
}
```

---

## ⚔️ **Comparing Enums**

* Use `==` for comparison (type-safe).
* `equals()` also works, since it’s overridden in `Enum`.

```java
Color c1 = Color.RED;
Color c2 = Color.RED;
System.out.println(c1 == c2);     // true
System.out.println(c1.equals(c2)); // true
```

⚠️ Enums with the same **ordinal** but different **types** are *not equal*.

---

## 🧭 **Summary / Key Takeaways**

| Concept                            | Description                            |
| ---------------------------------- | -------------------------------------- |
| **Enum**                           | Defines a fixed set of named constants |
| **values(), ordinal(), valueOf()** | Built-in enum methods                  |
| **Cannot extend classes**          | Enums already extend `Enum`            |
| **Can implement interfaces**       | Adds flexibility                       |
| **Private constructors**           | Prevents manual instantiation          |
| **Type-safe comparison**           | Use `==` or `equals()`                 |
| **Cannot create new objects**      | All constants created automatically    |

---

💡 **Pro Tip:**
Use enums for **limited constant sets** — like `Days`, `Seasons`, or `StatusCodes`.
They make your code **type-safe, readable, and maintainable**. 🌈

---

✨ *End of Notes — Enums in Java explained simply and colorfully!*
