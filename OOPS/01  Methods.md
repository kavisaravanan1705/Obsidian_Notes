# ☕ Java Notes — Functions & Methods

## 📌 Tags
`#java` `#functions` `#methods` `#oop` `#programming` `#basics` `#placement`

---

## 1. Function vs Method

> ⚠️ **This distinction is very important in Java!**

| | Function | Method |
|---|---|---|
| **Where defined** | Outside a class | Inside a class |
| **Used in** | C, C++ | Java ✅ |
| **Java uses?** | ❌ No standalone functions | ✅ Only methods |

### 🔑 Key Rule for Java:
- Java does **NOT have standalone functions**.
- **Everything is inside a class** → so we always call them **methods**.

**Example:**
```java
class Demo {
    void display() {   // This is a METHOD (not a function)
        System.out.println("Hello");
    }
}
```

---

## 2. Method Definition vs Method Calling

### ✍️ Method Definition
> Writing the **method logic** — what the method should do.

```java
void greet() {
    System.out.println("Hello Kavi");
}
```

---

### 📞 Method Calling
> **Invoking** the method to actually run it.

```java
class Demo {
    void greet() {
        System.out.println("Hello");
    }

    public static void main(String[] args) {
        Demo obj = new Demo();
        obj.greet();   // ← Method Calling
    }
}
```

> 💡 **How to call a method:**
> 1. Create an object → `Demo obj = new Demo();`
> 2. Use the object to call → `obj.greet();`

---

## 3. Void Function (No Return Type)

- Does **not return** any value.
- Uses the keyword `void`.

```java
void printMsg() {
    System.out.println("No return value");
}
```

> 🔑 `void` = **"I give nothing back"**

---

## 4. Parameters vs Arguments

> These two are commonly confused — know the difference!

| Term | Where | Meaning |
|---|---|---|
| **Parameter** | In method **definition** | Placeholder variable |
| **Argument** | In method **call** | Actual value passed |

**Example:**
```java
void add(int a, int b) {   // a, b → Parameters (placeholders)
    System.out.println(a + b);
}

add(5, 10);  // 5, 10 → Arguments (actual values)
```

> 💡 **Memory trick:**
> - **P**arameter = **P**laceholder (in definition)
> - **A**rgument = **A**ctual value (in call)

---

## 5. Parameterized Function
> A method that **takes inputs** (has parameters).

```java
void displayName(String name) {
    System.out.println(name);
}
```

---

## 6. Return Type Function
> A method that **returns a value** using the `return` keyword.

```java
int add() {
    return 5 + 3;
}
```

> ⚠️ The return type in the method signature (`int`) must **match** what you return.

---

## 7. Parameterized Non-Void Function
> A method that **takes input AND returns output**.

```java
int multiply(int a, int b) {
    return a * b;
}
```

---

## 8. 🔥 Types of Methods — Complete Summary

### Type 1️⃣ — Return Type WITH Parameters
> **Input + Output**

```java
int add(int a, int b) {
    return a + b;
}
```

---

### Type 2️⃣ — Return Type WITHOUT Parameters
> **No input, but gives output**

```java
int getNumber() {
    return 10;
}
```

---

### Type 3️⃣ — Non-Return Type WITH Parameters
> **Input only, no return**

```java
void printSum(int a, int b) {
    System.out.println(a + b);
}
```

---

### Type 4️⃣ — Non-Return Type WITHOUT Parameters
> **No input, no output**

```java
void greet() {
    System.out.println("Hello");
}
```

---

## 9. ⚡ Quick Revision Table

| Type | Has Parameters? | Has Return? | Example Signature |
|---|---|---|---|
| 1️⃣ | ✅ Yes | ✅ Yes | `int add(int a, int b)` |
| 2️⃣ | ❌ No | ✅ Yes | `int getNum()` |
| 3️⃣ | ✅ Yes | ❌ No | `void print(int a)` |
| 4️⃣ | ❌ No | ❌ No | `void greet()` |

---

## 10. 🗺️ Visual Concept Map

```
METHOD
 │
 ├── Has Return Value?
 │    ├── YES → Use a data type  (int, String, double...)
 │    │          Must use: return keyword
 │    └── NO  → Use void
 │
 └── Has Parameters?
      ├── YES → Parameterized method
      │          Values passed as Arguments during call
      └── NO  → Non-parameterized method
```

---

## 11. 💡 Placement Tips

### Most Asked Interview Topics:
- ✅ Difference between **parameter** and **argument**
- ✅ **Types of methods** (all 4 types)
- ✅ **Return type** usage

### Must Remember:
| Keyword | Meaning |
|---|---|
| `void` | Method returns **nothing** |
| `return` | Method **sends back a value** — must match declared data type |
| `int`, `String`, etc. | The **type of value** the method will return |

---

## 12. ❌ Common Beginner Mistakes

### Mistake 1 — Using `return` inside a `void` method
```java
// ❌ Wrong
void greet() {
    return "Hello";   // ERROR — void cannot return a value
}

// ✅ Correct
void greet() {
    System.out.println("Hello");
}
```

---

### Mistake 2 — Return type mismatch
```java
// ❌ Wrong
int getNum() {
    return "Hello";   // ERROR — declared int but returning String
}

// ✅ Correct
int getNum() {
    return 10;
}
```

---

### Mistake 3 — Calling method without creating an object
```java
// ❌ Wrong
greet();   // ERROR — method must be called through object

// ✅ Correct
Demo obj = new Demo();
obj.greet();
```

---



