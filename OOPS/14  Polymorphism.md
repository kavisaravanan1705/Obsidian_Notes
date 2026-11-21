# Polymorphism (Java)

> **Tags:** #java #oops #polymorphism #function-overloading #compile-time #runtime

---

## 👉 What is Polymorphism?

- **Poly** = many
- **Morph** = forms
- **Polymorphism** = One thing → many forms

### 👶 Example (Baby Level)

Same person 👩

- At home → daughter
- At college → student
- At job → employee

> 👉 Same person, different roles = **Polymorphism**

---

## 💻 In Java (Your Case)

> 👉 Same function name → different behavior

```java
display()
display(int a)
```

👉 Same name = `display` 👉 Different forms = **Polymorphism**

---

## 🔥 Function Overloading (Important)

> **Definition (Exam Ready):** Function with **same name** but **different parameters** is called **Function Overloading**

---

## 📌 Your Code (Explained Line by Line)

```java
class text {
    public static void main(String[] args) {
        fine obj = new fine();   // create object

        obj.display();           // call 1
        obj.display(4);          // call 2
    }
}

class fine {

    void display() {
        System.out.println("Hello");
    }

    void display(int a) {
        System.out.println(a);
    }
}
```

### ⚙️ What Happens Step-by-Step

**`obj.display();`**

- No parameter → calls `display()`
- Output → `Hello`

**`obj.display(4);`**

- Has integer → calls `display(int a)`
- Output → `4`

### 🧾 Output

```
Hello
4
```

---

## 🧠 Method Signature (IMPORTANT)

> 👉 **Signature = method name + parameters**

|Method|Signature|
|---|---|
|`display()`|`display()`|
|`display(int a)`|`display(int)`|

> ❗ **Return type is NOT part of signature** ❌

---

## 🎯 Real-Time Examples (Easy)

### 📱 Example 1: Mobile Calculator

```java
add(int a, int b)
add(double a, double b)
add(int a, int b, int c)
```

> 👉 Same function name → `add` 👉 Different inputs → works differently

### 🖨️ Example 2: Print Function

```java
print(String text)
print(int number)
print(double value)
```

> 👉 Same function → prints different types

### 🚗 Example 3: Vehicle

```java
start()
start(String key)
```

> 👉 Bike → button start 👉 Car → key start

---

## 🔥 When We Use This (Real Life Use)

**When:**

- Same action but different inputs
- Reduce code duplication
- Improve readability

**Used in:**

- Calculator apps
- APIs
- Libraries (like Java Math class)

---

## 🧠 Simple Memory Trick

> 👉 **Same name + different inputs = Overloading**

---

## ⚡ Final 2-Line Answer (Exam)

> 👉 Polymorphism is the ability of a method to take multiple forms. 👉 Function overloading is a type of polymorphism where methods have same name but different parameters.

---

## ❓ Are Polymorphism & Function Overloading the Same?

> ❌ **NO**, they are NOT same ✔️ **Function Overloading is a TYPE of Polymorphism**

### 🎯 Simple Understanding (Baby Level)

- **Polymorphism** = Big concept (umbrella ☂️)
- **Function Overloading** = One type inside it

### 👶 Example

- Polymorphism = Fruits 🍎🍌🍇
- Function Overloading = Only Apple 🍎

---

## 📊 Difference Table: Polymorphism vs Function Overloading

|Feature|Polymorphism|Function Overloading|
|---|---|---|
|Meaning|One thing → many forms|Same method name, different parameters|
|Type|Concept|Implementation (type)|
|When decided|Compile-time & Run-time|Compile-time only|
|Example|Overloading + Overriding|Only Overloading|

---

## 💻 Example to Understand

### 🔹 Polymorphism (General Idea)

```java
display()
display(int a)
display(String s)
```

> 👉 Same method → many forms = **Polymorphism**

### 🔹 Function Overloading

```java
void display() { }
void display(int a) { }
```

> 👉 This is **one type** of polymorphism

---

## 🧠 Method Signature (VERY IMPORTANT)

> **Definition (Exam Ready):** Method signature = **method name + parameter list**

### 📌 From Your Code

```java
void display()
void display(int a)
```

|Method|Signature|
|---|---|
|`display()`|`display()`|
|`display(int a)`|`display(int)`|

### ❗ Important Points

**Signature INCLUDES ✔️**

- Method name
- Number of parameters
- Type of parameters

**Signature does NOT include ❌**

- Return type
- Variable names

### ⚠️ Wrong Example (Not Overloading)

```java
int display()
void display()
```

> ❌ ERROR (same signature)

---

## ⚡ Final 2-Line Answer (Exam)

> 👉 Polymorphism is the ability of a method to take multiple forms. 👉 Function overloading is a **compile-time polymorphism** where methods have same name but different parameters.

---

# Compile Time vs Run Time

---

## 🧠 Baby Level Explanation

|Phase|Analogy|
|---|---|
|📝 Compile Time|Teacher checking your exam paper **before** submission|
|▶️ Run Time|Writing exam **in the hall**|

### 🎯 Simple Definition

**Compile Time:**

- Before execution
- Java checks code (errors, method selection)

**Run Time:**

- During execution
- Program actually runs and gives output

---

## 💻 Example (Your Code)

```java
obj.display();
obj.display(4);
```

> 👉 Java decides which method to call **BEFORE** running ✔️ So this is **Compile Time**

---

## 🔥 Why Overloading = Compile Time?

👉 Because Java decides based on:

- Number of arguments
- Type of arguments

✔️ **BEFORE execution**

---

## 👀 Real-Life Examples

### 🍽️ Hotel Order (Compile Time)

> 👉 You say:
> 
> - "Bring coffee" ☕
> - "Bring 2 coffees" ☕☕
> 
> 👉 Waiter understands **immediately** (before action) 👉 This is like **Compile Time**

### 🚗 Driving (Run Time)

> 👉 While driving:
> 
> - If obstacle comes → you turn
> - If signal red → you stop
> 
> 👉 Decisions happen **during action** 👉 This is **Run Time**

---

## 📊 Easy Difference Table

|Feature|Compile Time|Run Time|
|---|---|---|
|When|Before execution|During execution|
|What happens|Code checking, method selection|Actual execution|
|Example|Function Overloading|Function Overriding|

### 🧠 Memory Trick

> 👉 **Compile** = Check + Decide before run 👉 **Run** = Execute + Act now

---

## ⚡ Final 2-Line Answer (Exam)

> 👉 Compile time is the phase where the program is checked and methods are resolved before execution. 👉 Run time is the phase where the program is executed and output is produced.

---

# Compile Time vs Run Time — Technical

---

## 🧠 Compile Time (Technical)

> **Definition:** Compile time is the phase where the **source code is converted into bytecode** by the Java compiler (`javac`).

**What happens:**

- Syntax checking
- Type checking
- Method binding (for overloading)
- Error detection

> ✔️ Also called: **Static Binding / Early Binding**

### 💻 Example (Compile-Time Polymorphism)

```java
class Test {
    void display() {
        System.out.println("Hello");
    }

    void display(int a) {
        System.out.println(a);
    }

    public static void main(String[] args) {
        Test obj = new Test();
        obj.display();     // resolved at compile time
        obj.display(10);   // resolved at compile time
    }
}
```

> 👉 Compiler decides:
> 
> - `display()`
> - `display(int)`
> 
> ✔️ **BEFORE execution**

---

## 🧠 Run Time (Technical)

> **Definition:** Run time is the phase where the **compiled bytecode is executed by JVM**.

**What happens:**

- Object creation
- Method execution
- Dynamic method dispatch (overriding)

> ✔️ Also called: **Dynamic Binding / Late Binding**

### 💻 Example (Run-Time Polymorphism)

```java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal obj = new Dog();   // parent reference, child object
        obj.sound();              // resolved at runtime
    }
}
```

> 👉 JVM decides:
> 
> - Whether to call `Animal.sound()` or `Dog.sound()`
> 
> ✔️ Decision happens at **runtime**

---

## 📊 Technical Difference Table

|Feature|Compile Time|Run Time|
|---|---|---|
|Binding|Static Binding|Dynamic Binding|
|Decision|By Compiler|By JVM|
|Polymorphism|Overloading|Overriding|
|Speed|Faster|Slightly slower|
|Flexibility|Less|More|

---

## 🧠 Key Technical Point

> 👉 **Compile Time** → Method call resolved using **reference + parameters** 👉 **Run Time** → Method call resolved using **object type**

---

## ⚡ Final Exam Answer (2–3 lines)

> 👉 Compile time is the phase where method calls are resolved by the compiler using **static binding**, such as in function overloading. 👉 Run time is the phase where method calls are resolved during execution by the JVM using **dynamic binding**, such as in method overriding.

---

