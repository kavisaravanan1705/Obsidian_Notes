# 📘 Object Creation — Real-Time Examples (Placement Notes)

---

## 🔹 Core Concept — Real-Time Thinking

|Term|Real-World Meaning|
|---|---|
|**Class**|Blueprint / Empty form structure|
|**Object**|Actual filled form / real instance|

> 💡 **Think of it this way:**  
> The **Application Form** printed on paper = Class (template)  
> Each **student's filled form** = Object (real data)

---

## 🔹 Real-Time Example 1 — 📝 Application Form

### Class = The Empty Form Template

```java
class Application {
    String name;
    int age;

    void display() {
        System.out.println(name + " " + age);
    }
}
```

---

### Objects = Each Student's Filled Form

```java
Application a1 = new Application();
Application a2 = new Application();
```

### Fill the Forms (Assign Data)

```java
a1.name = "Kavi";   a1.age = 19;
a2.name = "Arun";   a2.age = 20;
```

### Show the Forms (Display)

```java
a1.display();   // Output: Kavi 19
a2.display();   // Output: Arun 20
```

### 🧠 Visual

```
Application Class (empty form template)
          │
    ┌─────┴─────┐
    ↓           ↓
   a1           a2
name = Kavi   name = Arun
age  = 19     age  = 20

✅ Each object = one student's filled form
✅ Data is completely separate
```

---

## 🔹 Real-Time Example 2 — 🏥 Hospital System

> A hospital has **Patients** and **Doctors** — both are different classes with their own objects.

---

### 🧩 Class — Patient

```java
class Patient {
    String name;
    int age;

    void display() {
        System.out.println(name + " " + age);
    }
}
```

### Patient Objects

```java
Patient p1 = new Patient();
Patient p2 = new Patient();

p1.name = "Ravi";   p1.age = 45;
p2.name = "Meena";  p2.age = 30;
```

```
Patient Class
      │
  ┌───┴───┐
  ↓       ↓
 p1       p2
Ravi,45  Meena,30

✅ Each patient = one object
```

---

### 🧩 Class — Doctor

```java
class Doctor {
    String name;
    String specialization;

    void display() {
        System.out.println(name + " " + specialization);
    }
}
```

### Doctor Objects

```java
Doctor d1 = new Doctor();
Doctor d2 = new Doctor();
```

```
Doctor Class
      │
  ┌───┴───┐
  ↓       ↓
 d1       d2
(Doctor 1) (Doctor 2)

✅ One class → Many doctors
```

---

### 🧠 Full Hospital System Picture

```
Hospital System
├── Patient Class
│     ├── p1 → Ravi, 45
│     └── p2 → Meena, 30
│
└── Doctor Class
      ├── d1 → Doctor 1
      └── d2 → Doctor 2
```

> ✅ Different real-world things = Different classes  
> ✅ Each real-world person = One object

---

## 🔹 Getting User Input — Real-Time (Application Form)

> Instead of hardcoding, let users fill the form themselves using `Scanner`.

### ✅ Full Program

```java
import java.util.Scanner;

class Application {
    String name;
    int age;

    void getData() {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter name: ");
        name = sc.nextLine();

        System.out.print("Enter age: ");
        age = sc.nextInt();
    }

    void display() {
        System.out.println(name + " " + age);
    }
}

class Main {
    public static void main(String[] args) {

        Application a1 = new Application();
        Application a2 = new Application();

        a1.getData();   // first student fills form
        a2.getData();   // second student fills form

        a1.display();   // show first student's data
        a2.display();   // show second student's data
    }
}
```

---

### 🔍 Step-by-Step Flow

```
1. a1 = new Application()  → empty form created for student 1
2. a2 = new Application()  → empty form created for student 2

3. a1.getData()  → student 1 types name & age → stored in a1
4. a2.getData()  → student 2 types name & age → stored in a2

5. a1.display()  → prints student 1's data
6. a2.display()  → prints student 2's data

✅ Works like filling multiple forms independently
```

---

## 🔹 Key Understanding — VERY IMPORTANT

|Real World|Java Equivalent|
|---|---|
|Application form template|Class|
|Each student's filled form|Object|
|Patient in a hospital|Object of `Patient` class|
|Doctor in a hospital|Object of `Doctor` class|
|Filling the form|Assigning data / calling `getData()`|

---

> ⭐ **Golden Rule:**
> 
> ```
> One Class → Unlimited Objects
> Each Object → Different Real-World Data
> ```

---

## 🔹 One-Line Summaries

> 🔵 **Class** = Template (empty form, blueprint)  
> 🟢 **Object** = Real-world instance (filled form, actual patient, actual doctor)  
> 🟡 **One class** → Many objects, each with its own separate data  
> 🔑 **Access** → `objectName.field` or `objectName.method()`

---

## 📋 Cheatsheet

```
┌─────────────────────────────────────────────────────────────┐
│         OBJECT CREATION — REAL-TIME CHEATSHEET              │
├─────────────────────────────────────────────────────────────┤
│  Class   = Blueprint / empty template                       │
│  Object  = Real instance (new ClassName())                  │
│                                                             │
│  Example 1 — Application Form:                             │
│    Application a1 = new Application();  → student 1 form   │
│    Application a2 = new Application();  → student 2 form   │
│                                                             │
│  Example 2 — Hospital:                                      │
│    Patient p1, p2  → different patients                     │
│    Doctor  d1, d2  → different doctors                      │
│                                                             │
│  User Input:                                                │
│    Use Scanner inside getData() method                      │
│    Call: a1.getData() → user fills their own data           │
│                                                             │
│  Golden Rule:                                               │
│    One class → Unlimited objects                            │
│    Each object → Separate, independent data                 │
└─────────────────────────────────────────────────────────────┘
```

---

