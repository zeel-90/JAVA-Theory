# 🚀 Everything About Interfaces in Java

## 📘 What Is an Interface?

An **interface** in Java is a **contract** that defines behaviors a
class must follow.\
It can contain: - 🟦 Abstract methods\
- 🟩 Default methods\
- 🟧 Static methods\
- 🟨 Private methods\
- 🟥 Constants

------------------------------------------------------------------------

## 🔍 What an Interface Can Contain

### 1. 🟦 Abstract Methods

Methods without a body.

``` java
void run();
```

------------------------------------------------------------------------

### 2. 🟩 Default Methods (Java 8+)

Methods with a body.

``` java
default void show() { 
    System.out.println("Default show"); 
}
```

------------------------------------------------------------------------

### 3. 🟧 Static Methods (Java 8+)

Cannot be inherited; must be called using the interface name.

``` java
static void print() { 
    System.out.println("Static method"); 
}
```

------------------------------------------------------------------------

### 4. 🟨 Private Methods (Java 9+)

Used internally inside the interface.

``` java
private void helper() {
    System.out.println("Helper method");
}
```

------------------------------------------------------------------------

### 5. 🟥 Constants

All variables in an interface are automatically:

-   `public`
-   `static`
-   `final`

Example:

``` java
int MAX = 100;
```

------------------------------------------------------------------------

## 📏 Rules of Interfaces

-   ❌ Cannot have constructors\
-   ✔ A class can implement **multiple interfaces**\
-   ✔ Methods are **public by default**\
-   ✔ Interfaces can extend **multiple interfaces**\
-   ❌ Cannot have normal instance fields (only constants)

------------------------------------------------------------------------

## 🎯 Why Interfaces Are Used

-   ✔ To define a **contract**\
-   ✔ To support **multiple inheritance**\
-   ✔ To achieve **loose coupling**\
-   ✔ For **polymorphism**

------------------------------------------------------------------------

## 🔬 Types of Interface Methods (Summary Table)

  Method Type   Body?   Inherited by Class?   Notes
  ------------- ------- --------------------- -----------------------------------
  🟦 Abstract   ❌ No   ✔ Yes                 Must be overridden
  🟩 Default    ✔ Yes   ✔ Yes                 Can override
  🟧 Static     ✔ Yes   ❌ No                 Called using InterfaceName.method
  🟨 Private    ✔ Yes   ❌ No                 Used internally only

------------------------------------------------------------------------

## 🛠 Complete Example (All Features)

``` java
interface Vehicle {

    int MAX_SPEED = 180;  // constant

    void start();         // abstract method

    default void fuel() { // default method
        System.out.println("Vehicle fuel");
    }

    static void service(){ // static method
        System.out.println("Vehicle service");
    }

    private void helper(){ // private method
        System.out.println("Helper method");
    }
}

class Car implements Vehicle {

    public void start() {
        System.out.println("Car starting...");
    }

    @Override
    public void fuel() {  // overriding default method
        System.out.println("Car fuel");
    }
}
```

------------------------------------------------------------------------

## ⚔ Interface vs Abstract Class (Quick Comparison)

  Feature                  Interface        Abstract Class
  ------------------------ ---------------- -----------------------------
  Abstract methods         ✔                ✔
  Default/static methods   ✔                ✔
  Variables                Constants only   Yes
  Constructor              ❌ No            ✔ Yes
  Multiple inheritance     ✔ Yes            ❌ No
  Purpose                  Contract         Base class with shared code

------------------------------------------------------------------------

## ⭐ Final Interview Summary

> "An interface in Java defines a contract that classes must follow.\
> It can include abstract, default, static, and private methods, along
> with constants.\
> Interfaces enable multiple inheritance and are used to define shared
> behavior across unrelated classes."# 🚀 Everything About Interfaces in Java

## 📘 What Is an Interface?

An **interface** in Java is a **contract** that defines behaviors a
class must follow.\
It can contain: - 🟦 Abstract methods\
- 🟩 Default methods\
- 🟧 Static methods\
- 🟨 Private methods\
- 🟥 Constants

------------------------------------------------------------------------

## 🔍 What an Interface Can Contain

### 1. 🟦 Abstract Methods

Methods without a body.

``` java
void run();
```

------------------------------------------------------------------------

### 2. 🟩 Default Methods (Java 8+)

Methods with a body.

``` java
default void show() { 
    System.out.println("Default show"); 
}
```

------------------------------------------------------------------------

### 3. 🟧 Static Methods (Java 8+)

Cannot be inherited; must be called using the interface name.

``` java
static void print() { 
    System.out.println("Static method"); 
}
```

------------------------------------------------------------------------

### 4. 🟨 Private Methods (Java 9+)

Used internally inside the interface.

``` java
private void helper() {
    System.out.println("Helper method");
}
```

------------------------------------------------------------------------

### 5. 🟥 Constants

All variables in an interface are automatically:

-   `public`
-   `static`
-   `final`

Example:

``` java
int MAX = 100;
```

------------------------------------------------------------------------

## 📏 Rules of Interfaces

-   ❌ Cannot have constructors\
-   ✔ A class can implement **multiple interfaces**\
-   ✔ Methods are **public by default**\
-   ✔ Interfaces can extend **multiple interfaces**\
-   ❌ Cannot have normal instance fields (only constants)

------------------------------------------------------------------------

## 🎯 Why Interfaces Are Used

-   ✔ To define a **contract**\
-   ✔ To support **multiple inheritance**\
-   ✔ To achieve **loose coupling**\
-   ✔ For **polymorphism**

------------------------------------------------------------------------

## 🧩 Types of Interface Methods (Summary Table)

| Method Type | Has Body? | Inherited by Class? | Notes |
|------------|-----------|----------------------|--------|
| 🟦 Abstract | ❌ No | ✔️ Yes | Must be overridden |
| 🟩 Default  | ✔️ Yes | ✔️ Yes | Can override |
| 🟧 Static   | ✔️ Yes | ❌ No  | Called using InterfaceName.method |
| 🟨 Private  | ✔️ Yes | ❌ No  | Used internally only |


------------------------------------------------------------------------

## 🛠 Complete Example (All Features)

``` java
interface Vehicle {

    int MAX_SPEED = 180;  // constant

    void start();         // abstract method

    default void fuel() { // default method
        System.out.println("Vehicle fuel");
    }

    static void service(){ // static method
        System.out.println("Vehicle service");
    }

    private void helper(){ // private method
        System.out.println("Helper method");
    }
}

class Car implements Vehicle {

    public void start() {
        System.out.println("Car starting...");
    }

    @Override
    public void fuel() {  // overriding default method
        System.out.println("Car fuel");
    }
}
```

------------------------------------------------------------------------

## ⚔ Interface vs Abstract Class (Quick Comparison)

| Feature                 | Interface        | Abstract Class              |
|-------------------------|------------------|------------------------------|
| Abstract methods        | ✔ Yes            | ✔ Yes                        |
| Default/static methods  | ✔ Yes            | ✔ Yes                        |
| Variables               | Constants only   | Can have variables           |
| Constructor             | ❌ No            | ✔ Yes                        |
| Multiple inheritance    | ✔ Yes            | ❌ No                        |
| Purpose                 | Contract         | Base class with shared code  |

------------------------------------------------------------------------

## ⭐ Final Interview Summary

> "An interface in Java defines a contract that classes must follow.\
> It can include abstract, default, static, and private methods, along
> with constants.\
> Interfaces enable multiple inheritance and are used to define shared
> behavior across unrelated classes."
