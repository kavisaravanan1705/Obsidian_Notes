## Multiple Inheritance using Interface

> 👉 A class can implement **two or more interfaces** at the same time 👉 This is how Java achieves **multiple inheritance** (not possible with classes)

---

### 💻 Full Program with Comments

java

```java
// Interface 1 — Father side
interface Father {
    void speak();   // public + abstract by default (no body)
    void run();     // public + abstract by default (no body)
}

// Interface 2 — Mother side
interface Mother {
    void speak();   // same method name as Father — that's okay in interface
    void run();     // same method name as Father — no conflict here
}

// Son implements BOTH Father and Mother
// Son must implement ALL methods from BOTH interfaces
class Son implements Father, Mother {   // multiple interfaces separated by comma

    public void speak() {               // ✅ implements speak() from BOTH Father & Mother
        System.out.println("I am speaking");
        // only ONE method written — satisfies both interfaces at once
    }

    public void run() {                 // ✅ implements run() from BOTH Father & Mother
        System.out.println("I am running");
        // same here — one method, satisfies both
    }
}

class text {
    public static void main(String[] args) {

        Son s = new Son();   // ✅ Son is a normal class — object allowed

        s.speak();           // calls speak() defined in Son → prints "I am speaking"
        s.run();             // calls run() defined in Son  → prints "I am running"
    }
}
```

---

### 🧾 Output

```
I am speaking
I am running
```

---

### 🧠 Why No Conflict Even Though Both Interfaces Have Same Method?

> ❓ Both `Father` and `Mother` have `speak()` and `run()` — won't it cause an error?

> ✅ **No conflict** — because both interfaces only **declare** the method (no body) 👉 `Son` writes the body **once** → it satisfies both interfaces at the same time

|Interface|Method Declared|Body?|
|---|---|---|
|Father|`speak()`, `run()`|❌ No body|
|Mother|`speak()`, `run()`|❌ No body|
|Son|`speak()`, `run()`|✅ Body written once|

---

### 📊 Multiple Inheritance Flow

```
Father (interface)        Mother (interface)
   speak(), run()            speak(), run()
         ↘                  ↙
          Son implements both
          speak() { ... }    ← one method satisfies both
          run()   { ... }    ← one method satisfies both
```

---

### ⚠️ Key Insight

> 👉 In Java, **class cannot extend two classes** (multiple inheritance ❌) 👉 But **class CAN implement two interfaces** ✅ 👉 This is why interfaces exist — to give multiple inheritance safely

||extends (class)|implements (interface)|
|---|---|---|
|Multiple?|❌ Only one|✅ Many allowed|
|Example|`class A extends B`|`class A implements B, C`|

---

## 🔹 Key Points (Quick Revision ⚡)

|Point|Detail|
|---|---|
|Interface =|100% abstraction|
|Methods|`public + abstract` by default|
|Variables|`public static final` by default|
|Keyword|`implements`|
|Rule|Must override **all** methods|
|Use case|Real projects — for flexibility & switching|

---

## 🧠 Memory Trick

> 👉 **"Interface = contract"** 👉 **"Whoever signs (implements) must follow all rules (methods)"**

---

## 🎯 Final Short Answer (Exam Ready)

> 👉 Interface is a blueprint that provides **100% abstraction** with all methods public and abstract by default. 👉 A class uses `implements` keyword and **must override all methods** of the interface.