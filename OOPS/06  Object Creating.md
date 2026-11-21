# 📘 Object Creation & User Input — Placement Notes

---

## 🔹 Creating an Object

### Syntax

```java
ClassName objectName = new ClassName();
```

### Example

```java
Student s1 = new Student();
```

### Breaking It Down

|Part|Meaning|
|---|---|
|`Student`|The Class (blueprint)|
|`s1`|The Object (instance)|
|`new`|Allocates memory in RAM|
|`Student()`|Constructor — sets up the object|

---

## 🔹 Creating Multiple Objects from One Class

> 💡 **One class → Many objects** — just like one blueprint can build many houses.

```java
Student s1 = new Student();
Student s2 = new Student();
Student s3 = new Student();
```

### Assign Values to Each Object

```java
s1.name = "Kavi";   s1.age = 20;
s2.name = "Raj";    s2.age = 21;
s3.name = "Priya";  s3.age = 19;
```

### 🔑 Important Rule

> ✅ Each object has its **own separate data**  
> ✅ Changes in `s1` will **NOT affect** `s2` or `s3`

---

### 🧠 Visual — Each Object is Independent

```
Student Class (Blueprint)
        │
   ┌────┴────┬─────────┐
   ↓         ↓         ↓
  s1        s2        s3
name=Kavi  name=Raj  name=Priya
age=20     age=21    age=19
```

---

## 🔹 Getting User Input Using a Method

> Instead of hardcoding values, we take input from the user using `Scanner` inside a method.

### ✅ Full Program

```java
import java.util.Scanner;

class Student {
    String name;
    int age;

    // Method to take input from user
    void getData() {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter name: ");
        name = sc.nextLine();

        System.out.print("Enter age: ");
        age = sc.nextInt();
    }

    // Method to display data
    void display() {
        System.out.println(name + " " + age);
    }
}

class Main {
    public static void main(String[] args) {

        Student s1 = new Student();

        s1.getData();    // takes input from user
        s1.display();    // prints the data
    }
}
```

---

### 🔍 How It Works — Step by Step

```
1. Student s1 = new Student();   → object created in memory

2. s1.getData();                 → user types name and age
                                    stored inside s1

3. s1.display();                 → prints s1's name and age
```

---

## 🔹 Multiple Objects with User Input

```java
Student s1 = new Student();
Student s2 = new Student();

s1.getData();    // user enters data for s1
s2.getData();    // user enters data for s2

s1.display();    // prints s1's data
s2.display();    // prints s2's data
```

> ✅ Each object takes its **own separate input**  
> ✅ `s1` and `s2` are completely **independent**

---

### 🧠 Flow Diagram — Multiple Objects with Input

```
main()
  │
  ├── s1 = new Student()
  │     └── s1.getData()  → user types: "Kavi", 20
  │
  ├── s2 = new Student()
  │     └── s2.getData()  → user types: "Raj", 21
  │
  ├── s1.display()  → Output: Kavi 20
  └── s2.display()  → Output: Raj 21
```

---

## 🔹 Key Points — Placement Focus

|Concept|What to Remember|
|---|---|
|Create object|`ClassName obj = new ClassName();`|
|Multiple objects|Same class, each has different data|
|User input|Use `Scanner` inside a method (`getData()`)|
|Access method|`objectName.methodName()`|
|Objects are independent|Changing `s1` does NOT affect `s2`|

---

## 🔹 One-Line Summaries (VERY IMPORTANT)

> 🔵 **Object** = `new ClassName()` → allocates memory  
> 🟢 **Multiple objects** = same class, different data, fully independent  
> 🟡 **User input** = use `Scanner` inside a method, call with `object.getData()`  
> 🔑 **Access rule** = `objectName.field` or `objectName.method()`

---

## 📋 Cheatsheet

```
┌─────────────────────────────────────────────────────────────┐
│            OBJECT CREATION & INPUT CHEATSHEET               │
├─────────────────────────────────────────────────────────────┤
│  Create object:                                             │
│    ClassName obj = new ClassName();                         │
│                                                             │
│  Assign values directly:                                    │
│    obj.name = "Kavi";                                       │
│    obj.age  = 20;                                           │
│                                                             │
│  Take user input via method:                                │
│    obj.getData();    ← Scanner inside getData()             │
│                                                             │
│  Display:                                                   │
│    obj.display();                                           │
│                                                             │
│  Multiple objects:                                          │
│    Student s1 = new Student();  → own data                  │
│    Student s2 = new Student();  → own data (independent)   │
│                                                             │
│  Golden rule:                                               │
│    One class → Many objects → Each stores different values  │
└─────────────────────────────────────────────────────────────┘
```

---

