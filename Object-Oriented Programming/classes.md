# 🧱 **Classes and Objects in Java**

> A **class** is a *template or blueprint* for creating objects.
> An **object** is an *instance* of a class — it has **state, identity, and behavior**.

---

## 🧩 **Understanding Classes**

A class defines a new **data type** that can be used to create objects.

```java
class Box {
    double width;
    double height;
    double depth;
}
```

You can create objects (instances) of this class to represent real entities.

---

## 🧠 **Class vs Object**

| Concept      | Description                                    |
| ------------ | ---------------------------------------------- |
| **Class**    | Logical structure or template (blueprint)      |
| **Object**   | Physical instance stored in memory             |
| **State**    | Data or attributes (e.g., width, height)       |
| **Behavior** | Actions or methods (e.g., calculateVolume())   |
| **Identity** | Unique memory reference distinguishing objects |

---

## ⚙️ **Creating and Using Objects**

The `.` (dot) operator links the object’s name with its variables or methods.

```java
Box mybox;        // Declare reference
mybox = new Box(); // Allocate memory for object
```

At first, `mybox` is just a **reference** (not an object).
`new Box()` allocates memory and returns a reference to that object.

> 🧠 The variable `mybox` stores the **memory address** of the actual `Box` object —
> but Java does not allow pointer manipulation, ensuring safety.

---

## 🚀 **Dynamic Memory Allocation with `new`**

```java
Box mybox = new Box();
```

Here:

* `Box` → class name
* `mybox` → reference variable
* `new Box()` → object creation (calls constructor)

🧩 **Formula:**

```java
classname classVar = new classname();
```

---

## 🧱 **Example: Creating and Accessing an Object**

```java
class Box {
    double width, height, depth;
}

class Main {
    public static void main(String[] args) {
        Box b = new Box();
        b.width = 5;
        b.height = 10;
        b.depth = 3;
        System.out.println("Volume: " + (b.width * b.height * b.depth));
    }
}
```

✅ **Output:**

```
Volume: 150.0
```

---

## 🧮 **Object Reference Behavior**

```java
Box b1 = new Box();
Box b2 = b1;
```

Both `b1` and `b2` refer to the **same object**.
Changes made through one reference are visible through the other.

⚠️ Assigning one object reference to another does **not** create a new object —
it only copies the reference (the memory address).

---

## 🔍 **Primitive vs Object Types**

You don’t use `new` for **primitive data types** (`int`, `char`, `double`, etc.)
because they are **not objects** — this improves performance.

---

## 💬 **Parameters and Arguments**

```java
int square(int i) {
    return i * i;
}
```

* **Parameter:** Variable defined in the method declaration (`i`)
* **Argument:** Value passed during the method call (`square(100)`)

---

## 🧭 **Summary / Key Takeaways**

| Concept                   | Description                                          |
| ------------------------- | ---------------------------------------------------- |
| **Class**                 | Blueprint defining object structure                  |
| **Object**                | Instance of a class with memory allocated at runtime |
| **new keyword**           | Allocates memory and returns reference               |
| **Dot operator (.)**      | Accesses object members                              |
| **Reference assignment**  | Copies the reference, not the object                 |
| **Primitive types**       | Not created with `new` for efficiency                |
| **Parameter vs Argument** | Definition vs value passed at call time              |

---

💡 **Pro Tip:**
Think of a class as a *cookie cutter* 🍪 and objects as *cookies*.
The cutter (class) defines the shape — each cookie (object) is an individual instance!

---

✨ *End of Notes — Classes and Objects in Java made visual and simple!*
