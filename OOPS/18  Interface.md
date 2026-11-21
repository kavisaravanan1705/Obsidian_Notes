
# Interface in Java

> **Tags:** #java #oops #interface #abstraction #multiple-inheritance

---

## 📌 What is Interface?

> 👉 An interface is a **blueprint of a class** 👉 Used to achieve **100% abstraction**

- Contains only **abstract methods** (no body) by default
- A class uses the `implements` keyword to use an interface

---

## 🔹 Syntax

```java
interface InterfaceName {
    returnType methodName();  // abstract method (public + abstract by default)
}
```

---

## 🔹 Keywords Behind the Scene

Even if you write:

```java
interface Father {
    void talk();
}
```

Java **internally** treats it as:

```java
interface Father {
    public abstract void talk();  // auto-added by Java
}
```

> ⚠️ Java **automatically** adds `public abstract` — you don't need to write it

---

## 💻 Your Program (Step by Step)

### Interface — Father

```java
interface Father {
    void talk();    // public + abstract by default
    void speak();   // public + abstract by default
}
```

### Class — implements Father

```java
class Interface implements Father {

    public void talk() {              // ✅ must be public
        System.out.println("I am talking");
    }

    public void speak() {             // ✅ must be public
        System.out.println("I am speaking");
    }
}
```

### Main Method

```java
class text {
    public static void main(String[] args) {
        Interface i = new Interface();
        i.talk();
        i.speak();
    }
}
```

---

## 🧾 Output

```
I am talking
I am speaking
```

---

## ⚠️ Important Rule — Why `public` in Child Class?

> ❓ Why must we write `public` when implementing?

Methods in interface are by default:

```java
public abstract void talk();
```

So while implementing, you **MUST** write `public`:

```java
public void talk()   // ✅ correct
```

### ❌ Wrong:

```java
void talk()   // default access — ERROR ❌
```

> 👉 Error occurs because you are **reducing the access level** 👉 `public → default` is **NOT allowed** in Java

### ✅ Rule:

|Location|Access Level|
|---|---|
|Interface method|`public` (auto)|
|Implementing class|**must be** `public`|

---

## 🔹 Why Use Interface?

|Reason|Explanation|
|---|---|
|Abstraction|Hides implementation details|
|Multiple Inheritance|A class can implement multiple interfaces|
|Common Behavior|Defines a contract all classes must follow|
|Flexibility|Switch implementations without changing logic|

---

## 🔹 class vs interface — Keywords

|Relationship|Keyword|
|---|---|
|class → class|`extends`|
|class → interface|`implements`|
|interface → interface|`extends`|

> ⚠️ Inside interface, **all methods must be abstract** (no body)

---

## 🎯 Real-Time Examples

### 1️⃣ Payment System

```java
interface Payment {
    void pay();
}

class GPay implements Payment {
    public void pay() {
        System.out.println("Paid using GPay");
    }
}

class PhonePe implements Payment {
    public void pay() {
        System.out.println("Paid using PhonePe");
    }
}
```

> 👉 Same method `pay()` → different implementations per class

---

### 2️⃣ USB Device (Real Hardware Concept)

```java
interface USB {
    void connect();
}

class Mouse implements USB {
    public void connect() {
        System.out.println("Mouse connected");
    }
}

class Keyboard implements USB {
    public void connect() {
        System.out.println("Keyboard connected");
    }
}
```

> 👉 Laptop doesn't care — mouse or keyboard 👉 It just calls `connect()` and it works ✅

---

### 3️⃣ Company Project (IMPORTANT FOR PLACEMENT 🚀)

```java
interface Database {
    void connect();
}

class MySQL implements Database {
    public void connect() {
        System.out.println("Connected to MySQL");
    }
}

class MongoDB implements Database {
    public void connect() {
        System.out.println("Connected to MongoDB");
    }
}
```

> 👉 Company can **switch database easily** 👉 Only the implementation changes — not the main logic

---

## 🔹 Key Points (Quick Revision ⚡)

|Point|Detail|
|---|---|
|Interface =|100% abstraction|
|Methods|`public + abstract` by default|
|Variables|`public static final` by default|
|Keyword|`implements`|
|Rule|Must override **all** methods|
|Use case|Real projects — for flexibility & switching|

---

## 🧠 Memory Trick

> 👉 **"Interface = contract"** 👉 **"Whoever signs (implements) must follow all rules (methods)"**

---

## 🎯 Final Short Answer (Exam Ready)

> 👉 Interface is a blueprint that provides **100% abstraction** with all methods public and abstract by default. 👉 A class uses `implements` keyword and **must override all methods** of the interface.

---

