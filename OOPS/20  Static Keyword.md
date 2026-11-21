# Static in Java

when we use static keyword ?
when we want to access the method without using object , in that time we use static keyword
we can access the method without creating the boject by using static keyword

---

## 🔹 What is `static` in Java?

> 👉 `static` means **belongs to the class, not to the object**

- No need to create object to access it
- Shared by all objects

---

## 🔹 Where We Use `static`?

---

### 1. Static Variable

> 👉 **Definition:** A static variable is a **class-level variable** that is **shared among all objects** of the class.

👉 Same value shared for all objects

```java
class Student {
    static String college = "Anna University";
}
```

✔ Use when:

- Common data (same for all objects)
- Example: college name, company name

---

### 2. Static Method

> 👉 **Definition:** A static method is a method that **belongs to the class** and can be **called without creating an object**.

👉 Can be called without object

```java
class Demo {
    static void show() {
        System.out.println("Hello");
    }
}

public class Test {
    public static void main(String[] args) {
        Demo.show(); // no object
    }
}
```

✔ Use when:

- Method does not depend on object data
- Utility functions (like calculations)

---

### 3. Static Block

> 👉 **Definition:** A static block is a block of code that is **executed only once** when the class is **loaded into memory**.

👉 Runs only once when class is loaded

```java
class Demo {
    static {
        System.out.println("Static block executed");
    }
}
```

✔ Use when:

- Initialize static variables
- Run setup code once

---

### 4. Static Class (Inner Class only)

> 👉 **Definition:** A static class is a **nested class** that is declared static and can be accessed **without creating an object of the outer class**.

👉 Only inner class can be static

```java
class Outer {
    static class Inner {
        void display() {
            System.out.println("Static inner class");
        }
    }
}
```

---

## 🔹 Key Points (Very Important ⚡)

|Type|Level|
|---|---|
|Static|Class level|
|Non-static|Object level|

- Static methods **cannot** access non-static variables directly
- Memory saved (shared data)

---

## 💻 Your Program (with Comments as-is)

```java
class Animal {
    char name = 'A';
    static void sound() {  // Here i am using static keyword to use this method without creating an object
        System.out.println("Sound !!!");
    }
}

class Dog extends Animal {
    // char name = 'A';
    static void disp() { // since main function is static, so we declare this keyword before method so that both are static so we can access the method without object
        System.out.println("1111");
    }
}

class text {
    public static void main(String[] args) {
        // Animal a = new Animal();
        Animal.sound(); // Here I can access the method without object

        // Dog d = new Dog();
        Dog.disp();
    }
}
```

---

## 🧾 Output

```
Sound !!!
1111
```

---

## 🔹 Real-Time Examples

✔ **College Name**

- All students → same college 👉 use static variable

✔ **Math operations**

- No object needed 👉 use static methods (`Math.sqrt()`)

✔ **Main method**

```java
public static void main(String[] args)
```

> 👉 `static` because JVM calls it **without creating object**

---

## 🔹 One-Line Summary (for Exams)

> 👉 `static` is used to create **class-level members** that are shared among all objects and can be accessed **without creating an object**.

---

## 🧠 Memory Trick

> 👉 **"Static = class owns it"** 👉 **"Non-static = object owns it"**

---

_Next Topic → [[Final Keyword in Java]] 🚀_



