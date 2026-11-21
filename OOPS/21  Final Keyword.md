# Final Keyword in Java

> **Tags:** #java #final #oops #final-variable #final-method #final-class

---

## 📌 Definition

> `final` keyword is used to **restrict modification**. 👉 Once something is declared `final`, it **cannot be changed** further.

---

## 🔹 Where We Use `final`

We can use `final` in **3 places**:

---

### 1. Final Variable

> 👉 Value **cannot be changed** (constant)

```java
class Test {
    public static void main(String[] args) {
        final int a = 10;
        // a = 20; ❌ Error (cannot reassign)
        System.out.println(a);
    }
}
```

✔ Used when value should be fixed (like PI, constants)

---

### 2. Final Method

> 👉 Method **cannot be overridden**

```java
class Animal {
    final void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    // void sound() {} ❌ Error (cannot override final method)
}
```

✔ Used when you want to **protect method behavior**

---

### 3. Final Class

> 👉 Class **cannot be inherited**

```java
final class Animal {
}

// class Dog extends Animal {} ❌ Error (cannot extend final class)
```

✔ Used when you want to **stop inheritance**

---

## 🔹 Real-Time Examples

- `final` variable → constant values (e.g., tax rate)
- `final` method → security logic (cannot change)
- `final` class → classes like `String` (immutable)

---

## 🔹 Important Notes

- `final` variable must be **initialized once**
- For objects → **reference cannot change**, but object data can change

```java
final ArrayList<Integer> list = new ArrayList<>();
list.add(10); // ✅ allowed
// list = new ArrayList<>(); ❌ not allowed
```

---

## 🔹 Final Summary (2 lines – Exam Ready)

> `final` keyword is used to **restrict modification**. It can be applied to **variables** (constant), **methods** (no overriding), and **classes** (no inheritance).

---
