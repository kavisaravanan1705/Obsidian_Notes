# 📘 Constructor — Complete Notes

---

> 🧠 **One-Line Memory Trick:**  
> **"Constructor = Object create பண்ண ஓடனே value set பண்ணும் method"**  
> (When object is created → values are automatically set)

---

## 🔹 What is a Constructor?

> **Constructor** = A special method that **automatically runs** when an object is created, used to **initialize values**.

### Key Properties

- ✅ Automatically called when object is created — you don't call it manually
- ✅ Used to give initial/custom values to variables
- ✅ Same name as the class
- ✅ No return type (not even `void`)

---

## 🔹 Why Do We Need a Constructor?

### Without Constructor — Default Values Problem

```java
class Student {
    int id;
    String name;
}

public class Main {
    public static void main(String[] args) {

        Student s1 = new Student();

        System.out.println(s1.id);    // 0    ← useless default
        System.out.println(s1.name);  // null ← useless default
    }
}
```

> ⚠️ **Problem:** Java gives garbage/default values (`0`, `null`, `false`) — not useful!

---

### With Constructor — Proper Values ✅

```java
class Student {
    int id;
    String name;

    Student() {          // constructor — runs automatically
        id = 101;
        name = "Kavi";
    }
}

public class Main {
    public static void main(String[] args) {

        Student s1 = new Student();  // constructor runs here automatically

        System.out.println(s1.id);    // 101  ✅
        System.out.println(s1.name);  // Kavi ✅
    }
}
```

> ✅ **Solution:** Values are initialized the moment the object is created!

---

### 🧠 Simple Comparison

```
Without Constructor:
    Student s1 = new Student()  →  id = 0, name = null  ❌
    s1.id = 101;                →  manual assignment needed
    s1.name = "Kavi";

With Constructor:
    Student s1 = new Student()  →  id = 101, name = "Kavi" ✅
                                    (values set automatically!)
```

---

## 🔹 Types of Constructor

---

### 1️⃣ Default Constructor — No Parameters

> Used when **all objects need the same values**.

```java
class Student {
    int id;
    String name;

    Student() {          // default constructor (no parameters)
        id = 1;
        name = "Default";
    }
}
```

#### When to Use?

- ✔️ Same values for all objects
- ✔️ Simple initialization
- ✔️ You just want to avoid `null` / `0`

#### Flow

```
Student s1 = new Student()  →  id = 1, name = "Default" ✅
Student s2 = new Student()  →  id = 1, name = "Default" ✅
(both get same values)
```

---

### 2️⃣ Parameterized Constructor — Takes Values from User

> Used when **each object needs different values**.

```java
class Student {
    int id;
    String name;

    Student(int i, String n) {   // parameterized constructor
        id = i;
        name = n;
    }
}

public class Main {
    public static void main(String[] args) {

        Student s1 = new Student(101, "Kavi");   // values passed here
        Student s2 = new Student(102, "Ram");

        System.out.println(s1.name);   // Kavi
        System.out.println(s2.name);   // Ram
    }
}
```

#### When to Use?

- ✔️ Each object needs **different values**
- ✔️ Values decided at the time of object creation

#### Flow

```
Student s1 = new Student(101, "Kavi")
    → constructor runs with i=101, n="Kavi"
    → id = 101, name = "Kavi" ✅

Student s2 = new Student(102, "Ram")
    → constructor runs with i=102, n="Ram"
    → id = 102, name = "Ram" ✅
```

---

## 🆚 Default vs Parameterized — Quick Comparison

|Feature|Default Constructor|Parameterized Constructor|
|---|---|---|
|Parameters|❌ No|✅ Yes|
|Values|Same for all objects|Different for each object|
|Flexibility|Less|More|
|Use case|Same starting values|Custom values per object|

```
Default:
    new Student()          → same values every time

Parameterized:
    new Student(101,"Kavi") → custom values each time
    new Student(102,"Ram")  → different custom values
```

---

## 🎯 When to Use Constructor — IMPORTANT

Use a constructor when:

|Situation|Why Constructor Helps|
|---|---|
|Want to initialize variables immediately|Values set at object creation|
|Don't want to forget assigning values|Constructor forces initialization|
|Want clean & readable code|No separate assignment lines needed|
|Object creation + value assignment together|Happens in one line|

---

## ⚡ Super Simple Summary

```
❌ Without Constructor:
    Step 1: Create object
    Step 2: Manually assign values (can forget!)

✅ With Constructor:
    Step 1: Create object → values set AUTOMATICALLY ✅
    (Both steps happen in one line!)
```

---

## 🔹 Key Points — Remember Forever 💯

- [ ] Constructor = same name as class, no return type
- [ ] Automatically called when object is created
- [ ] **Default constructor** → no parameters → same values for all objects
- [ ] **Parameterized constructor** → takes parameters → different values per object
- [ ] Without constructor → Java gives `0`, `null`, `false` (default values)
- [ ] With constructor → you control what values are set

---

## 📋 Cheatsheet

```
┌──────────────────────────────────────────────────────────────┐
│                  CONSTRUCTOR CHEATSHEET                      │
├──────────────────────────────────────────────────────────────┤
│  What: Special method — auto-runs when object is created     │
│  Why:  To set initial values (avoid 0/null defaults)         │
│                                                              │
│  Default Constructor:                                        │
│    Student() { id = 1; name = "Default"; }                  │
│    → same values for all objects                             │
│                                                              │
│  Parameterized Constructor:                                  │
│    Student(int i, String n) { id = i; name = n; }           │
│    → different values per object                             │
│                                                              │
│  Without constructor:                                        │
│    new Student() → id=0, name=null ❌                       │
│                                                              │
│  With constructor:                                           │
│    new Student()        → id=1, name="Default" ✅           │
│    new Student(101,"Kavi") → id=101, name="Kavi" ✅         │
│                                                              │
│  Memory Trick:                                               │
│  "Object create = Constructor runs = Values set" 🔥         │
└──────────────────────────────────────────────────────────────┘
```

---

