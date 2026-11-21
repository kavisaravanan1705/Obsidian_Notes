# 📘 Getter & Setter — Complete Notes

---

> 🎯 **One-Line Interview Answer:**  
> **"Setter is used to modify private data with control, while getter is used to safely access that data."**

---

## 🔹 Simple Definition

|Method|Purpose|
|---|---|
|**Getter**|READ (get) a private variable|
|**Setter**|UPDATE (set) a private variable|

---

## 🔹 Why Do We Need Getter & Setter?

> Because of **Encapsulation (Data Hiding)**

```
Step 1 → Make variable private  (no direct access from outside)
Step 2 → Use getter to READ it  (controlled reading)
Step 3 → Use setter to UPDATE it (controlled writing + validation)
```

---

## 🔹 Real-Time Example — 🏦 Bank Account

```
Balance = private  (you can't directly change it)

checkBalance() → Getter  (read the balance)
deposit(amount) → Setter  (update the balance safely)
```

> ✅ The bank doesn't let you directly change your balance — you must go through their system.  
> Same concept in code!

---

## 🔹 Basic Syntax

### ✅ Getter

```java
public int getVariableName() {
    return variableName;
}
```

### ✅ Setter

```java
public void setVariableName(int value) {
    this.variableName = value;
}
```

---

## 🔹 Core Example — Student Marks

```java
class Student {

    private int marks;   // 🔒 private — cannot access directly

    // ✅ Setter (set value)
    public void setMarks(int m) {
        marks = m;
    }

    // ✅ Getter (get value)
    public int getMarks() {
        return marks;
    }
}

public class Main {
    public static void main(String[] args) {

        Student s = new Student();

        // s.marks = 90;  ❌ ERROR — private, not allowed

        s.setMarks(90);                    // ✅ set through setter
        int result = s.getMarks();         // ✅ get through getter

        System.out.println(result);        // OUTPUT: 90
    }
}
```

### 🔍 Step-by-Step Flow

```
1. Student s = new Student()  → object created
2. s.setMarks(90)             → marks = 90 stored inside object
3. s.getMarks()               → returns 90
4. System.out.println(result) → prints 90
```

---

## 🔹 All Examples — Easy to Interview Level

---

### 📌 Example 1 — Basic (Name)

```java
class Person {

    private String name;

    public void setName(String n) {
        name = n;
    }

    public String getName() {
        return name;
    }
}

public class Main {
    public static void main(String[] args) {

        Person p = new Person();

        p.setName("Kavi");
        System.out.println(p.getName());   // Output: Kavi
    }
}
```

---

### 📌 Example 2 — With Validation ⭐ (Interview Favorite)

> Setter prevents wrong data from being stored.

```java
class Student {

    private int age;

    public void setAge(int a) {
        if (a > 0) {
            age = a;                              // ✅ valid
        } else {
            System.out.println("Invalid age");    // ❌ rejected
        }
    }

    public int getAge() {
        return age;
    }
}
```

### 🧠 Flow — Validation

```
s.setAge(20)   → a > 0 ? YES → age = 20 ✅
s.setAge(-5)   → a > 0 ? NO  → "Invalid age" ❌
```

---

### 📌 Example 3 — Bank Account (Real-Time 🔥)

```java
class BankAccount {

    private double balance;

    // Setter → deposit money
    public void setBalance(double amount) {
        if (amount > 0) {
            balance += amount;   // adds to existing balance
        }
    }

    // Getter → check balance
    public double getBalance() {
        return balance;
    }
}

public class Main {
    public static void main(String[] args) {

        BankAccount acc = new BankAccount();

        acc.setBalance(1000);   // deposit 1000
        acc.setBalance(500);    // deposit 500

        System.out.println(acc.getBalance());   // Output: 1500.0
    }
}
```

### 🧠 Flow

```
balance starts at 0
setBalance(1000) → balance = 0 + 1000 = 1000
setBalance(500)  → balance = 1000 + 500 = 1500
getBalance()     → returns 1500 ✅
```

---

### 📌 Example 4 — Read-Only (Only Getter)

> Sometimes we don't allow modification at all.

```java
class Company {

    private String companyName = "Google";

    // Only getter — no setter
    public String getCompanyName() {
        return companyName;
    }
}
```

> ✅ You can **read** the company name  
> ❌ You **cannot change** it (no setter exists)

---

### 📌 Example 5 — Write-Only (Only Setter) 🔐

> Rare but used for security (e.g., passwords).

```java
class Password {

    private String password;

    // Only setter — no getter
    public void setPassword(String p) {
        password = p;
    }
}
```

> ✅ You can **set** the password  
> ❌ You **cannot read** it back (no getter — security!)

---

### 📌 Example 6 — Multiple Variables

```java
class Employee {

    private String name;
    private int salary;

    // Setter for both
    public void setDetails(String n, int s) {
        name = n;
        salary = s;
    }

    // Getters for each
    public String getName() { return name; }
    public int getSalary()  { return salary; }
}
```

---

### 📌 Example 7 — `this` Keyword ⭐ (Interview Favorite)

> When the parameter name is **same** as the class variable — use `this` to differentiate.

```java
class Student {

    private int marks;

    public void setMarks(int marks) {
        this.marks = marks;   // this.marks = class variable
                              // marks = parameter value
    }

    public int getMarks() {
        return this.marks;
    }
}
```

### 🧠 `this` Explained

```
this.marks → refers to the class variable (private int marks)
marks      → refers to the method parameter (int marks)

Without 'this' → Java gets confused (both have same name!)
With 'this'    → clearly tells Java: "use the class variable" ✅
```

---

## 🔹 When to Use — Quick Decision Table

|Situation|What to Use|
|---|---|
|Hide data from outside|`private` + getter/setter|
|Validate input before storing|Setter with `if` condition|
|Read data safely|Getter|
|Prevent changing a value|Only Getter (no setter)|
|Prevent reading a value|Only Setter (no getter)|
|Security (passwords, secrets)|Write-only setter|

---

## 🔹 Key Points — Remember Forever 💯

- [ ] `private` → data hiding (no direct access)
- [ ] `getter` → read private data safely
- [ ] `setter` → update private data with control + validation
- [ ] `this` keyword → differentiates class variable from parameter
- [ ] Read-only → only getter, no setter
- [ ] Write-only → only setter, no getter
- [ ] Used for **security + control** in OOP & interviews

---

## 📋 Cheatsheet

```
┌─────────────────────────────────────────────────────────────┐
│               GETTER & SETTER CHEATSHEET                    │
├─────────────────────────────────────────────────────────────┤
│  private int marks;          → hidden variable              │
│                                                             │
│  Getter → public int getMarks() { return marks; }          │
│  Setter → public void setMarks(int m) { marks = m; }       │
│                                                             │
│  With validation:                                           │
│    if (m >= 0 && m <= 100) { marks = m; }                  │
│    else { "Invalid" }                                       │
│                                                             │
│  this.marks = marks;  → needed when param name = var name  │
│                                                             │
│  Read-only  → only getter (no setter)                       │
│  Write-only → only setter (no getter) → for passwords       │
│                                                             │
│  2-Line Exam Answer:                                        │
│  "Getter accesses private variables, setter modifies them.  │
│   They achieve encapsulation by controlling data access."   │
└─────────────────────────────────────────────────────────────┘
```

---

## Interview Practice: Getter and Setter in Java

### Problem: Employee Salary Validation

Interview question: Write a Java program to implement encapsulation for an `Employee` class using getters and setters.

Requirements:

1. Create a class named `Employee`.
    
2. Declare `name` as a `String` and `salary` as an `int`. Both variables must be `private`.
    
3. Create a getter and setter for `name`.
    
4. Create a getter and setter for `salary`.
    
5. The salary setter must accept only positive values. If the salary is zero or negative, do not update the salary.
    
6. In `main()`, create an employee, set the name to `"Arun"` and salary to `25000`, then print both values.
    

Expected output:

```
Employee Name: Arun
Employee Salary: 25000
```