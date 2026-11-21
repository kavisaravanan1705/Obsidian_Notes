# 🔁 Recursion in Java — Complete Notes

> **One-line definition:** Recursion = A function that calls itself.

---

## 🪞 What is Recursion?

Imagine standing between **two mirrors** — your reflection repeats endlessly inside each other.

That's exactly what recursion is in programming — a function keeps calling itself.

```java
static void printHello() {
    System.out.println("Hello");
    printHello();  // calling itself → INFINITE LOOP ❌
}
```

**Output:**

```
Hello
Hello
Hello
Hello
... (never stops)
```

> ⚠️ This is called **Infinite Recursion** — it's dangerous! We must stop it.

---

## 🛑 Base Condition — The Brake Pedal

To stop recursion, we always need a **Base Condition** (stopping condition).

> **Rule:** Every recursion MUST have:
> 
> 1. ✅ **Base Condition** → stops the recursion
> 2. 🔄 **Recursive Call** → calls itself

**Template:**

```java
static void function(int n) {

    if (condition)   // ← BASE CONDITION (stop here)
        return;

    function(n + 1); // ← RECURSIVE CALL (calls itself)
}
```

---

## 📌 Example 1 — Print 1 to 5 (Basic)

```java
static void printNumbers(int n) {

    if (n == 6)          // base condition: stop at 6
        return;

    System.out.println(n);

    printNumbers(n + 1); // recursive call
}

// Call:
printNumbers(1);
```

**Output:**

```
1
2
3
4
5
```

**How it flows:**

```
printNumbers(1) → print 1
printNumbers(2) → print 2
printNumbers(3) → print 3
printNumbers(4) → print 4
printNumbers(5) → print 5
printNumbers(6) → STOP ✋
```

---

## 📌 Example 2 — Print 5 to 1 (Reverse)

```java
static void printReverse(int n) {

    if (n == 0)           // base condition
        return;

    System.out.println(n);

    printReverse(n - 1);  // recursive call
}

// Call:
printReverse(5);
```

**Output:**

```
5
4
3
2
1
```

---

## 🧠 The Most Important Concept — Where You Print Changes Everything

> This is the **heart** of recursion. Read this carefully.

### 🔽 Going DOWN vs 🔼 Coming UP

When a recursive function runs, it goes through **two phases:**

|Phase|What Happens|
|---|---|
|**Going DOWN**|Function keeps calling itself (no printing yet if print is after call)|
|**Coming UP (Backtracking)**|Function returns back — this is where "after" prints happen|

---

### 🔥 Golden Rule

|Print Position|Output Order|
|---|---|
|**BEFORE** recursive call|Goes DOWN while printing → **3, 2, 1**|
|**AFTER** recursive call|Prints while coming UP → **1, 2, 3**|

---

### ✅ Print BEFORE → Output: 3, 2, 1

```java
static void printNum(int n) {

    if (n == 0) return;

    System.out.println(n);  // ← print BEFORE call

    printNum(n - 1);
}

// Call: printNum(3)
```

**Step-by-step:**

```
printNum(3) → print 3, then call printNum(2)
printNum(2) → print 2, then call printNum(1)
printNum(1) → print 1, then call printNum(0)
printNum(0) → STOP
```

**Output:** `3 → 2 → 1`

---

### ✅ Print AFTER → Output: 1, 2, 3

```java
static void printNum(int n) {

    if (n == 0) return;

    printNum(n - 1);        // ← call FIRST

    System.out.println(n);  // ← print AFTER
}

// Call: printNum(3)
```

**Step-by-step going DOWN (no print yet):**

```
printNum(3) → calls printNum(2)
printNum(2) → calls printNum(1)
printNum(1) → calls printNum(0)
printNum(0) → STOP ✋
```

**Now coming BACK UP (printing happens):**

```
back to printNum(1) → print 1
back to printNum(2) → print 2
back to printNum(3) → print 3
```

**Output:** `1 → 2 → 3`

---

### 🥞 Stack Diagram (Think of stacking plates)

**Going down (stacking):**

```
printNum(3)  ← waiting...
printNum(2)  ← waiting...
printNum(1)  ← waiting...
printNum(0)  ← STOP
```

**Coming back up (removing plates from top):**

```
printNum(1) → print 1  ✅
printNum(2) → print 2  ✅
printNum(3) → print 3  ✅
```

---

## 📌 Example 3 — Tricky One (n+1 with print AFTER)

```java
static void printNum(int n) {

    if (n == 6) return;     // stop at 6

    printNum(n + 1);        // call first

    System.out.println(n);  // print after
}

// Call: printNum(1)
```

**Going DOWN:**

```
printNum(1) → printNum(2) → printNum(3) → printNum(4) → printNum(5) → printNum(6) STOP
```

**Coming BACK UP (printing):**

```
printNum(5) → print 5
printNum(4) → print 4
printNum(3) → print 3
printNum(2) → print 2
printNum(1) → print 1
```

**Output:**

```
5
4
3
2
1
```

---

## 📌 Example 4 — Using User Input

```java
import java.util.Scanner;

class Main {

    static void printNum(int n) {

        if (n == 0)
            return;

        printNum(n - 1);       // call first (so we print in order 1,2,3...)

        System.out.println(n); // print after
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.println("Enter number:");
        int n = sc.nextInt();

        printNum(n);
    }
}
```

**Example — Input: 5**

```
Output:
1
2
3
4
5
```

**Memory flow if input = 3:**

```
printNum(3)
  printNum(2)
    printNum(1)
      printNum(0) → STOP
    ↑ print 1
  ↑ print 2
↑ print 3
```

---

## ⚠️ Important — Base Condition Controls What Gets Printed

```java
if (n == 4) return;
```

If condition stops at 4, then **4 is NOT printed** — because the function exits before reaching the print line.

|Stop Condition|Max Number Printed|
|---|---|
|`if (n == 4) return;`|3|
|`if (n == 5) return;`|4|
|`if (n == 6) return;`|5|

> **Rule:** Whatever number hits the base condition → that number is **skipped** (not printed).

---

## 🧪 Quick Practice Tests

### Test 1 — What is the output?

```java
static void test(int n) {
    if (n == 0) return;
    System.out.println(n);
    test(n - 1);
}
// Call: test(3)
```

<details> <summary>Click to reveal answer</summary>

```
3
2
1
```

Print is BEFORE recursive call → prints while going DOWN.

</details>

---

### Test 2 — What is the output?

```java
static void test(int n) {
    if (n == 0) return;
    test(n - 1);
    System.out.println(n);
}
// Call: test(3)
```

<details> <summary>Click to reveal answer</summary>

```
1
2
3
```

Print is AFTER recursive call → prints while coming UP (backtracking).

</details>

---

### Test 3 — What is the output?

```java
static void test(int n) {
    if (n == 4) return;
    System.out.println(n);
    test(n + 1);
}
// Call: test(1)
```

<details> <summary>Click to reveal answer</summary>

```
1
2
3
```

Stops at n==4, so 4 is never printed. Prints: 1, 2, 3.

</details>

---

## 📋 Summary Cheatsheet

```
┌─────────────────────────────────────────────────────────┐
│                   RECURSION RULES                       │
├─────────────────────────────────────────────────────────┤
│  1. Always have a BASE CONDITION (or infinite loop!)    │
│  2. Always have a RECURSIVE CALL (calls itself)         │
│  3. Print BEFORE call  → normal/descending order        │
│  4. Print AFTER call   → reverse/ascending order        │
│  5. Base condition number is NEVER printed              │
└─────────────────────────────────────────────────────────┘
```

---

## 🔜 Next Topic: Factorial Using Recursion

```
5! = 5 × 4 × 3 × 2 × 1 = 120
```

This is one of the most important recursion problems in interviews and exams!