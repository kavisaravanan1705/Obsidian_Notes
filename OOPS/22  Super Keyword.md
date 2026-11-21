# Super Keyword in Java

> **Tags:** #java #super #oops #inheritance #constructor

---

## 📌 Definition

> `super` keyword is used to refer **parent class (superclass) object**. 👉 It helps to access parent class **properties, methods, and constructors**.

---

## 🔹 Where We Use `super`

We use `super` in **3 main ways**:

---

### 1. Access Parent Class Variable

> 👉 Used when parent and child have **same variable name**

```java
class Animal {
    int x = 10;
}

class Dog extends Animal {
    int x = 20;

    void show() {
        System.out.println(super.x); // parent value (10)
        System.out.println(x);       // child value (20)
    }
}
```

---

### 2. Call Parent Class Method

> 👉 Used when method is **overridden**

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog sound");
    }

    void display() {
        super.sound(); // calls parent method
        sound();       // calls child method
    }
}
```

---

### 3. Call Parent Class Constructor

> 👉 Used to **initialize parent class**

```java
class Animal {
    Animal() {
        System.out.println("Animal constructor");
    }
}

class Dog extends Animal {
    Dog() {
        super(); // calls parent constructor
        System.out.println("Dog constructor");
    }
}
```

✔ Note:

- `super()` must be **first statement** in constructor
- If not written, Java **automatically calls it**

---

## 🔹 Real-Time Usage

- Reuse parent class code
- Avoid duplication
- Access overridden methods when needed

---

## 🔹 Important Points

- `super` works only in **inheritance**
- Cannot be used in **static context**
- Refers to **immediate parent only**

---

## 🔹 Final Summary (2 lines – Exam Ready)

> `super` keyword is used to refer to the **immediate parent class**. It is used to access parent **variables, methods, and constructors**.

---

_Next Topic → [[Exception Handling in Java]] 🚀_




# Java OOP — `super` Keyword

## 1. Definition

`super` is a keyword that refers to the **immediate parent class**. It is used to access parent-class variables, methods, and constructors.

## 2. Three Important Uses

### A. Access parent variable

Used when parent and child have variables with the same name.

```
class Parent {
    int number = 10;
}

class Child extends Parent {
    int number = 20;

    void show() {
        System.out.println(number);       // 20
        System.out.println(super.number); // 10
    }
}
```

### B. Call parent method

Used when the child overrides a parent method but also needs the parent's implementation.

```
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        super.sound();
        System.out.println("Dog barks");
    }
}
```

Output:

```
Animal sound
Dog barks
```

### C. Call parent constructor

Used to initialize the parent part of a child object.

```
class Animal {
    Animal(String name) {
        System.out.println(name);
    }
}

class Dog extends Animal {
    Dog() {
        super("Tommy");
        System.out.println("Dog constructor");
    }
}
```

Output:

```
Tommy
Dog constructor
```

## 3. Important Constructor Rules

- When a child object is created, the parent constructor runs before the child constructor.
    
- If you do not explicitly write a parent constructor call, Java inserts `super()` automatically.
    
- Automatic `super()` works only if the parent has an accessible no-argument constructor.
    
- If the parent has only a parameterized constructor, the child must explicitly call a matching constructor using `super(arguments)`.
    
- If no matching parent constructor exists, compilation fails.
    
- An explicit `super(...)` call must be the first statement in a constructor.
    

## 4. Why Does the Parent Constructor Run First?

When creating a child object, Java must initialize its parent-class portion before completing child initialization.

```
Dog d = new Dog();
```

Execution order:

1. Parent constructor
    
2. Child constructor
    

Both constructors execute, but only constructors containing print statements produce visible output.

## 5. Quick Revision Table

|Syntax|Purpose|
|---|---|
|`super.variable`|Access parent variable|
|`super.method()`|Call parent method|
|`super()`|Call parent no-argument constructor|
|`super(arguments)`|Call a matching parameterized parent constructor|

**Key to remember:** `super` refers to the parent class. Parent constructors run first, but parent methods do not run automatically when you call a child method.