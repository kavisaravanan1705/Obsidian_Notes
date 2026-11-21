# 📘 Programming Basics — OOP Placement Notes

---

## 🔹 Types of Programming

There are mainly **2 types** of programming:

---

### 1️⃣ Procedural Programming (POP)

- Program is written using **functions**
- Focus is on **step-by-step execution**
- Example languages: **C**

---

### 2️⃣ Object-Oriented Programming (OOP)

- Program is written using **objects and classes**
- Focus is on **real-world modeling**
- Example languages: **Java, C++, Python**

---

### 🆚 Quick Comparison

|Feature|Procedural (POP)|Object-Oriented (OOP)|
|---|---|---|
|Focus|Functions|Objects & Classes|
|Real-world modeling|❌ Hard|✅ Easy|
|Data security|❌ Weak|✅ Strong|
|Code reusability|❌ Difficult|✅ Easy|
|Example language|C|Java, C++, Python|

---

## 🔹 Why OOP? (IMPORTANT for Placements)

### ❌ Problems in Procedural Language

- Difficult to handle **complex real-world problems**
- **No proper data security**
- Code becomes **hard to manage & reuse**

---

### 🏦 Real-Time Example — Bank System

#### In Procedural Style:

```
deposit()       → separate functions
withdraw()      → separate functions
checkBalance()  → separate functions
```

> ⚠️ **Problem:** The data (balance) is **not protected**.  
> Anyone can directly change it → ❌ **Security issue!**

---

#### In OOP Style:

```
Class: BankAccount
├── balance  (private data — hidden from outside)
├── deposit()
└── withdraw()
```

> ✅ **Solution:** Balance is **private**.  
> Only allowed methods can touch it → ✅ **Safe & Organized!**

---

### ✅ OOP Solves These 3 Problems

|Problem|OOP Solution|
|---|---|
|No data security|Data made **private** inside class|
|Hard to manage code|Code organized into **classes & objects**|
|No real-world representation|Each real thing = one **class**|

---

## 🔹 Class and Its Members

### 🧩 What is a Class?

> **Class = Blueprint of an object**

Just like an architectural blueprint is not a house, but it defines how the house will be built — a class defines how an object will look and behave.

**Examples of classes:**

- `Car`
- `Student`
- `BankAccount`

---

### 🧩 Members of a Class

A class has **2 types of members:**

#### 1. Fields (Variables) — Store Data

```java
int age;
String name;
```

#### 2. Methods (Functions inside class) — Perform Actions

```java
void display() {
    System.out.println("Hello");
}
```

---

### 🧠 Simple Way to Remember

```
Class
├── Fields  → what it HAS  (data/attributes)
└── Methods → what it DOES (actions/behavior)

Example: Student class
├── Fields  → name, age, rollNo
└── Methods → display(), study(), attend()
```

---

## 🔹 Object Creation & Access — Step by Step

### ✅ Step 1 — Create the Class

```java
class Student {
    int age;
    String name;

    void display() {
        System.out.println(name + " " + age);
    }
}
```

---

### ✅ Step 2 — Create an Object

```java
Student s1 = new Student();
```

> **Object = Instance of a class**  
> `s1` is one specific student created from the `Student` blueprint.

---

### ✅ Step 3 — Access Members Using Dot (`.`)

**Access Fields (set data):**

```java
s1.age = 20;
s1.name = "Kavi";
```

**Access Methods (perform action):**

```java
s1.display();   // Output: Kavi 20
```

---

### 🔑 Rule to Remember

```
objectName.fieldName    → to access data
objectName.methodName() → to call a method
```

---

### 🧠 Full Flow Diagram

```
Class (Blueprint)
      ↓
   new keyword creates
      ↓
   Object (s1)
      ↓
   s1.name = "Kavi"   ← set field
   s1.display()       ← call method
```

---

## 🔹 Key Terms — Quick Reference

|Term|Meaning|Example|
|---|---|---|
|**Class**|Blueprint/Template|`Student`, `Car`|
|**Object**|Real instance of a class|`Student s1 = new Student();`|
|**Field**|Variable inside class (data)|`int age;`|
|**Method**|Function inside class (action)|`void display()`|
|**`.` (dot)**|Used to access members|`s1.age`, `s1.display()`|

---

## 🔹 One-Line Summaries (VERY IMPORTANT for Exams)

> 🔵 **Procedural** → Focus on **functions**, step-by-step execution  
> 🟢 **OOP** → Focus on **objects**, real-world problems solved easily  
> 🧩 **Class** → Blueprint of an object  
> 📦 **Object** → Instance (real copy) of a class  
> 📋 **Fields** → Data stored in a class  
> ⚙️ **Methods** → Actions/behaviour of a class

---

## 📋 Full Cheatsheet

```
┌─────────────────────────────────────────────────────────────┐
│                  OOP BASICS CHEATSHEET                      │
├─────────────────────────────────────────────────────────────┤
│  POP  → functions, step-by-step, C                         │
│  OOP  → objects & classes, Java / C++ / Python             │
│                                                             │
│  Class  = Blueprint                                         │
│  Object = Instance of class (new ClassName())              │
│  Field  = data variable inside class                       │
│  Method = function inside class                             │
│                                                             │
│  Access: objectName.field    or    objectName.method()     │
│                                                             │
│  OOP solves:                                                │
│    ✅ Data security (private fields)                        │
│    ✅ Code reusability (classes reused)                     │
│    ✅ Real-world modeling (1 thing = 1 class)               │
└─────────────────────────────────────────────────────────────┘
```

---

