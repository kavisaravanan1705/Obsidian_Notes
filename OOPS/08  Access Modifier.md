# 📘 Access Modifiers & Setter — Ultra Clear Notes

---

> 🎯 **Golden One-Liner:**  
> **"Private protects → Setter controls → Public exposes"**

---

## 🔹 Overview — All 4 Access Modifiers at a Glance

|Modifier|Same Class|Same Package|Subclass (Child)|Anywhere|
|---|---|---|---|---|
|`public`|✅|✅|✅|✅|
|`protected`|✅|✅|✅|❌|
|`default` _(no keyword)_|✅|✅|❌|❌|
|`private`|✅|❌|❌|❌|

---

## 🔹 1. `public` — Open to Everyone

### ✅ Meaning

> Accessible from **anywhere** — same class, other class, any package.

### 🧠 Real-Time Example

> **ATM Screen** → Anyone can see and use the options. Nothing is hidden.

### 💻 Code

```java
class Student {

    public String name;       // public variable

    public void display() {   // public method
        System.out.println("Name: " + name);
    }
}

class Main {
    public static void main(String[] args) {

        Student s = new Student();

        s.name = "Kavi";   // ✅ allowed (public variable)
        s.display();       // ✅ allowed (public method)
    }
}
```

### 🧠 Flow

```
Main class
    └── creates Student object
          ├── s.name = "Kavi"  ✅ (public — direct access allowed)
          └── s.display()      ✅ (public — can call from anywhere)
```

---

## 🔹 2. `private` — Hidden Inside the Class 🔥

### ✅ Meaning

> Accessible **only inside the same class**. Cannot be touched from outside.

### 🧠 Real-Time Example

> **Bank Balance** → You cannot directly see or change someone's balance. You must go through proper methods.

---

### ❌ Wrong Way — No Protection

```java
class Bank {
    public int balance;   // public — no protection ❌
}

class Main {
    public static void main(String[] args) {

        Bank b = new Bank();

        b.balance = -5000;  // ❌ allowed but WRONG — negative balance!
    }
}
```

> ⚠️ **Problem:** Anyone can set invalid values directly. No control at all.

---

### ✅ Correct Way — Private + Controlled Access

```java
class Bank {

    private int balance;   // hidden from outside ✅

    // setter — controls HOW balance is set
    public void setBalance(int amount) {
        if (amount > 0) {
            balance = amount;         // ✅ valid
        } else {
            System.out.println("Invalid amount");  // ❌ rejected
        }
    }

    // getter — controls HOW balance is read
    public int getBalance() {
        return balance;
    }
}

class Main {
    public static void main(String[] args) {

        Bank b = new Bank();

        // b.balance = 5000;  ❌ ERROR — private, cannot access directly

        b.setBalance(5000);                        // ✅ set through setter
        System.out.println(b.getBalance());        // ✅ get through getter
    }
}
```

### 🧠 Flow — How Private + Setter Works

```
Outside (Main class)
    │
    ├── b.balance = -5000    ❌ BLOCKED (private)
    │
    └── b.setBalance(-5000)  → enters setter
              │
              ├── amount > 0 ? NO  → "Invalid amount" printed ❌
              └── amount > 0 ? YES → balance = amount ✅
```

---

### 🔥 Why Use `private` If We Have Functions?

> This is a **very common interview question!**

|Without `private`|With `private`|
|---|---|
|`b.balance = -10000` ❌ — anyone sets wrong values|`b.setBalance(-10000)` ❌ — rejected by validation|
|No control|Full control through setter|
|Data can be corrupted|Data is always valid|

**3 Reasons to Use `private`:**

1. 🛡️ **Prevent** direct wrong access
2. ✅ **Add validation** logic (only allow valid values)
3. 🔒 **Secure** the data

---

## 🔹 3. Setter & Getter Methods

### ✅ Setter — Set/Update a Private Variable

> Used when: variable is `private`, you need validation, you want to control input.

### ✅ Getter — Read a Private Variable

> Used when: you want to allow reading, but not direct modification.

### 💻 Code

```java
class Student {

    private int age;   // private — cannot access directly

    // setter — validates and sets age
    public void setAge(int age) {
        if (age > 0) {
            this.age = age;                      // ✅ valid age
        } else {
            System.out.println("Invalid age");   // ❌ rejected
        }
    }

    // getter — returns age
    public int getAge() {
        return age;
    }
}

class Main {
    public static void main(String[] args) {

        Student s = new Student();

        s.setAge(20);                           // ✅ set value
        System.out.println(s.getAge());         // ✅ get value → 20
    }
}
```

### 🧠 `this` Keyword Explained

```
this.age = age;

this.age → the class variable (private int age)
age      → the parameter passed into setAge(int age)

Without 'this', Java gets confused — both have the same name!
```

---

## 🔹 4. `protected` — Family Access Only

### ✅ Meaning

> Accessible in: **same class + same package + subclass (child class)**  
> NOT accessible outside the package by unrelated classes.

### 🧠 Real-Time Example

> **Family property** → Only family members (child, parent) can access. Strangers cannot.

### 💻 Code

```java
class Parent {
    protected int money = 10000;   // protected — only for family
}

class Child extends Parent {      // Child is a subclass of Parent

    void show() {
        System.out.println(money); // ✅ accessible (child class)
    }
}

class Main {
    public static void main(String[] args) {

        Child c = new Child();
        c.show();   // Output: 10000
    }
}
```

### 🧠 Flow

```
Parent class
    └── protected int money = 10000

Child class (extends Parent)
    └── can access money ✅ (child = family member)

Unrelated class (different package)
    └── cannot access money ❌ (stranger)
```

---

## 🔹 5. `protected` vs `public`

|Feature|`public`|`protected`|
|---|---|---|
|Access|Open to **everyone**|Limited — family only|
|Use case|Open APIs, UI methods|Inheritance, shared logic|
|Real example|ATM screen|Family property|

> 🔵 **Public** → Fully open door  
> 🟡 **Protected** → Door open only for family

---

## 🔹 6. `default` — Same Package Only

### ✅ Meaning

> No keyword written = default access.  
> Accessible **only within the same package**.

### 💻 Code

```java
class Student {
    int marks;   // no keyword = default access
}
```

> ✅ Accessible inside same package  
> ❌ NOT accessible from other packages

---

## 🔹 Final Quick Revision Checklist

- [ ] `public` → access from **anywhere**
- [ ] `private` → only **inside same class**
- [ ] `protected` → **inheritance + same package**
- [ ] `default` _(no keyword)_ → **same package only**
- [ ] `setter` → safely **update** private data (with validation)
- [ ] `getter` → safely **read** private data

---

## 📋 Full Cheatsheet

```
┌──────────────────────────────────────────────────────────────┐
│              ACCESS MODIFIERS CHEATSHEET                     │
├──────────────────────────────────────────────────────────────┤
│  public    → anywhere ✅✅✅✅  (ATM screen)                 │
│  protected → same class + package + child ✅✅✅            │
│  default   → same class + package ✅✅                      │
│  private   → same class only ✅  (bank balance)             │
│                                                              │
│  Setter → public method to SET private variable             │
│           + validates the value before setting              │
│  Getter → public method to GET private variable             │
│                                                              │
│  Why private + setter?                                       │
│    Without → b.balance = -5000  ❌ no control               │
│    With    → b.setBalance(-5000) → rejected by validation ✅ │
│                                                              │
│  🎯 "Private protects → Setter controls → Public exposes"   │
└──────────────────────────────────────────────────────────────┘
```

---


