# Abstract Class & Abstract Method

> **Tags:** #java #oops #abstract-class #abstract-method #inheritance

---

## 🔹 What is Abstract Class?

> 👉 **Abstract class = incomplete class**

- We **CANNOT** create an object for abstract class
- Used **only for inheritance** (as a base/parent class)
- Can contain:
    - Abstract methods
    - Normal methods

```java
abstract class Computer {
}
```

### ❌ Wrong — This gives ERROR:

```java
Computer c = new Computer(); // ❌ Error
```

---

## 🔹 What is Abstract Method?

> 👉 **Method without body**

```java
abstract void display();
```

- No `{ }` — only declaration
- Child class **must** write code for it

---

## 🧩 Full Idea (Very Important)

> 👉 **Parent says:** _"I have a method… but I don't know how it works"_
> 
> 👉 **Child says:** _"I will complete it"_

---

## ❗ Important Rules

|#|Rule|
|---|---|
|1|Abstract class → ❌ no object|
|2|Abstract method → ❌ no body|
|3|Child **must** implement abstract method|
|4|If child doesn't implement → child also becomes `abstract`|
|5|If a class has abstract method → class **must** be `abstract`|

---

## 🔹 Your Program Flow

```
Computer (abstract)
   ↓
Hp extends Computer  → NOT abstract, no display() → inherits it unimplemented
   ↓
dell extends Hp      → adds turnOff(), still no display()
   ↓
acer extends dell    → ✅ finally implements display()
```

---

## 💻 Code — Step by Step

### Step 0 — Abstract Parent Class

```java
abstract class Computer {
    abstract void display();   // incomplete method — no body

    void turnOn() {
        System.out.println("Light is turning On");
    }
}
```

> 👉 `display()` has no body → it's abstract 👉 `turnOn()` has body → it's a normal method

---

### Step 1 — Hp (Not Abstract — Object Possible ✅)

```java
class Hp extends Computer {
    // no display() here
    // but Hp is NOT abstract
}
```

> 👉 `Hp` inherits from `Computer` but does **NOT** implement `display()` 👉 `Hp` is **not** declared abstract — so we **can** create its object 👉 This works because `display()` will be resolved further down the chain

---

### Step 2 — dell (No Error Yet)

```java
class dell extends Hp {
    void turnOff() {
        System.out.println("Light is turning off");
    }
}
```

> 👉 Still no `display()` — but no error yet 👉 The chain is still going...

---

### Step 3 — acer ✅ (Completes the Work)

```java
class acer extends dell {
    void display() {
        System.out.println("Nice display");
    }
}
```

> 👉 **Finally** someone implemented the method ✅ 👉 Now the class is **complete** — no more abstract pending

---

### 🚀 Main Method

```java
class text {
    public static void main(String[] args) {

        Hp h = new Hp();   // ✅ allowed — Hp is NOT abstract
        h.turnOn();        // inherited from Computer

        dell d = new dell();
        d.turnOff();       // defined in dell

        acer a = new acer();
        a.display();       // implemented in acer
    }
}
```

> 👉 `Hp` object is **allowed** because `Hp` is a normal class (not abstract) 👉 `h.turnOn()` works because `Hp` inherits `turnOn()` from `Computer`

---

## 📋 Full Program (Complete Code)

```java
abstract class Computer {              // abstract class
    abstract void display();           // abstract method — no body

    void turnOn() {
        System.out.println("Light is turning On");
    }
}

class Hp extends Computer {           // here we inherit the abstract class with hp class to call the method , now we can create obj since it is not abstract class

       }
}

class dell extends Hp {
    void turnOff() {
        System.out.println("Light is turning off");
    }
}

class acer extends dell {
    void display() {                   // ✅ implements abstract method
        System.out.println("Nice display");
    }
}

class text {
    public static void main(String[] args) {

        Hp h = new Hp();               // ✅ allowed
        h.turnOn();                    // inherited from Computer

        dell d = new dell();
        d.turnOff();                   // defined in dell

        acer a = new acer();
        a.display();                   // implemented in acer
    }
}
```

---

```
Light is turning On
Light is turning off
Nice display
```

> 👉 `Light is turning On` → from `h.turnOn()` (inherited by Hp from Computer) 👉 `Light is turning off` → from `d.turnOff()` (defined in dell) 👉 `Nice display` → from `a.display()` (implemented in acer)

---

## 🔥 One Line Logic

> 👉 **"Until someone writes the method → the chain continues"**

---

## 🔹 Key Points Summary

|Class|Type|Implements `display()`?|Object Possible?|
|---|---|---|---|
|`Computer`|`abstract`|❌ declared only|❌ No|
|`Hp`|normal|❌ not implemented|✅ Yes|
|`dell`|normal|❌ not implemented|✅ Yes|
|`acer`|normal|✅ finally implemented|✅ Yes|

> ⚠️ **Key Insight:** Even though `Hp` and `dell` don't implement `display()`, they are **not abstract** — so objects can be created. Java only errors if you try to **call** the unimplemented abstract method directly.

---

## 🎯 Final Short Answer (Exam Ready)

> 👉 Abstract class is a class that **cannot be instantiated** and is used for inheritance. 👉 Abstract method must be **implemented in subclass**.

---

## 🧠 Memory Trick

> 👉 **"Abstract = pending work"** 👉 **"Child = finishes work"**

---

