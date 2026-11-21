# 📘 Inheritance — Technical Notes

---

## 🧸 What is Inheritance?

> **Inheritance means taking things from parents**

### 👨‍👩‍👧 Real-life Example

- You get eyes, hair, height from your parents
- You didn't create them — you inherited them

✔ Same in programming!

---

## 💻 In Java (Super Simple)

- One class = **Parent**
- Another class = **Child**
- Child can use parent's things

---

## 🐶 Basic Example

### Parent Class

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating");
    }
}
```

### Child Class

```java
class Dog extends Animal {
    void bark() {
        System.out.println("Dog is barking");
    }
}
```

### Main Class

```java
class Main {
    public static void main(String[] args) {
        Dog d = new Dog();

        d.eat();   // from parent 👈
        d.bark();  // from child 👈
    }
}
```

### 🤯 What Happened Here?

```
Dog  → is the child
Animal → is the parent

Dog can:
    ✅ bark()  → its own method
    ✅ eat()   → inherited from parent (Animal)

👉 Dog didn't write eat() again → REUSE
```

---

## 🎯 One-Line Definition (Exam)

> **"Inheritance is the process where one class acquires the properties and methods of another class."**

---

## 🧠 Why We Use It?

- ✅ Reuse code
- ✅ Reduce duplication
- ✅ Easy to maintain

### 🔥 Super Simple Summary

> **Child = Parent + Extra Features**

---

## 📘 Technical Notes

---

## 🔹 Definition

- Inheritance is an OOP concept where one class (child/subclass) acquires properties and methods of another class (parent/superclass).
- Achieved using the keyword: `extends`

---

## 🔹 Syntax

```java
class Parent {
    // properties & methods
}

class Child extends Parent {
    // additional properties & methods
}
```

---

## 🔹 Key Terms

|Term|Meaning|
|---|---|
|**Superclass (Parent Class)**|Class whose properties are inherited|
|**Subclass (Child Class)**|Class that inherits|
|**`extends`**|Keyword used for inheritance|

---

## 🔹 Example (Basic)

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog is barking");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();

        d.eat();   // inherited method
        d.bark();  // own method
    }
}
```

### Output

```
Animal is eating
Dog is barking
```

---

## 🔹 Commands (How to Run)

```bash
javac Main.java   // compile
java Main         // run
```

---

## 🔹 Types of Inheritance in Java

---

### 1️⃣ Single Inheritance

```java
class A {
    void show() {
        System.out.println("Class A");
    }
}

class B extends A {
    void display() {
        System.out.println("Class B");
    }
}
```

```
Structure:
    A
    │
    B
```

---

### 2️⃣ Multilevel Inheritance

```java
class A {
    void show() {
        System.out.println("Class A");
    }
}

class B extends A {
    void display() {
        System.out.println("Class B");
    }
}

class C extends B {
    void print() {
        System.out.println("Class C");
    }
}
```

```
Structure:
    A  ← grandparent
    │
    B  ← parent
    │
    C  ← child
```

---

### 3️⃣ Hierarchical Inheritance

```java
class A {
    void show() {
        System.out.println("Class A");
    }
}

class B extends A {
    void display() {
        System.out.println("Class B");
    }
}

class C extends A {
    void print() {
        System.out.println("Class C");
    }
}
```

```
Structure:
        A  ← parent
       / \
      B   C  ← both inherit from A
```

---

## 🔹 Important Points

- ⚠️ Java does **NOT** support multiple inheritance using classes
- ✅ Use **interfaces** for multiple inheritance
- ✅ Constructor of **parent class runs first**
- ✅ Use `super` keyword to access parent class

---

## 🔹 Key Points — Remember Forever 💯

- [ ] Inheritance = child gets parent's properties & methods
- [ ] Keyword → `extends`
- [ ] Parent = Superclass | Child = Subclass
- [ ] Child can use parent's methods + add its own
- [ ] Multiple inheritance via class → ❌ NOT allowed
- [ ] Multiple inheritance via interface → ✅ Allowed
- [ ] Parent constructor runs **first**
- [ ] `super` → access parent's method or constructor

---

## 📋 Cheatsheet

```
┌──────────────────────────────────────────────────────────────┐
│                  INHERITANCE CHEATSHEET                      │
├──────────────────────────────────────────────────────────────┤
│  Definition:                                                 │
│  Child class acquires parent class properties & methods      │
│                                                              │
│  Keyword: extends                                            │
│    class Dog extends Animal { }                              │
│                                                              │
│  Types:                                                      │
│    Single       → A → B                 ✅                  │
│    Multilevel   → A → B → C            ✅                  │
│    Hierarchical → A → B  &  A → C      ✅                  │
│    Multiple     → A + B → C            ❌ (use Interface)   │
│                                                              │
│  Important:                                                  │
│    Parent constructor runs FIRST                             │
│    super → access parent class                               │
│    private members → NOT inherited                           │
│                                                              │
│  Golden Formula:                                             │
│  Child = Parent's features + Child's own features           │
└──────────────────────────────────────────────────────────────┘
```

---

