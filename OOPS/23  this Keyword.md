# This Keyword in Java

> **Tags:** #java #this #oops #constructor #method-chaining

---

## 📌 Definition

> `this` keyword is used to refer **current class object**. 👉 It means **"this current object"**.

---

## 🔹 Where We Use `this`

We use `this` in **5 important ways**:

---

### 1. Refer Current Class Variable

> 👉 Used when **local variable** and **instance variable** have same name

```java
class Student {
    int id;

    Student(int id) {
        this.id = id; // current object variable
    }
}
```

✔ Avoids confusion between local & instance variables

---

### 2. Call Current Class Method

```java
class Test {
    void display() {
        System.out.println("Hello");
    }

    void show() {
        this.display(); // calling method
    }
}
```

✔ Optional (Java automatically assumes it)

---

### 3. Call Current Class Constructor

> 👉 Used for **constructor chaining**

```java
class Test {
    Test() {
        this(10);
        System.out.println("Default constructor");
    }

    Test(int x) {
        System.out.println("Parameterized constructor");
    }
}
```

✔ `this()` must be **first statement**

---

### 4. Pass Current Object as Argument

```java
class Test {
    void show(Test obj) {
        System.out.println("Method called");
    }

    void display() {
        show(this);
    }
}
```

---

### 5. Return Current Object

```java
class Test {
    Test show() {
        return this;
    }
}
```

✔ Used in **method chaining**

---

## 🔹 Real-Time Usage

- Used in constructors (very common)
- Used in setters (`this.value = value`)
- Used in method chaining (like builders)

---

## 🔹 Important Points

- Refers to **current object only**
- Cannot be used in **static methods**
- Helps to write **clean and readable code**

---

## 🔹 Final Summary (2 lines – Exam Ready)

> `this` keyword refers to the **current class object**. It is used to access **variables, methods, constructors**, and pass or return the current object.

---

