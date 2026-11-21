# 🔁 Recursion — `return`, Function Names & Factorial Logic

---

## ❓ Why `return`? What Does It Do?

> **One-line answer:** `return` = **send the answer back** to whoever called the function.

---

### 🔥 Case 1 — Simple return (non-recursive)

```java
static int giveNumber() {
    return 10;
}

// Call:
int x = giveNumber();
// x = 10 ✅
```

`return` sends `10` back → stored in `x`.

---

### 🔥 Case 2 — `void` (no return)

```java
static void test() {
    System.out.println(10);  // only prints, cannot store
}
```

> ⚠️ `void` functions can only **print**. They **cannot send values back**.

---

### 🔥 Case 3 — Factorial with `return` (Recursion)

```java
static int fact(int n) {

    if (n == 1)
        return 1;          // base condition → send 1 back

    return n * fact(n-1);  // wait for smaller answer, multiply, send back
}
```

---

## 🧠 How `return n * fact(n-1)` Works — Step by Step

**Call:** `fact(3)`

### Phase 1 — Going DOWN (asking smaller problems)

```
fact(3) → needs fact(2)... waiting
  fact(2) → needs fact(1)... waiting
    fact(1) → returns 1  ✅ (base condition hit)
```

### Phase 2 — Coming UP (answers return back)

```
fact(1) → returns 1
fact(2) = 2 × 1 = 2  → returns 2
fact(3) = 3 × 2 = 6  → returns 6
```

**Final Answer: `6` ✅**

---

### 🎯 Real-Life Way to Think About It

> **Teacher asks:** What is `fact(3)`?
> 
> **You say:** I don't know directly, but…
> 
> - `fact(3) = 3 × fact(2)`
> - `fact(2) = 2 × fact(1)`
> - `fact(1) = 1` ← I know this!
> 
> **Now work back:**
> 
> - `fact(2) = 2 × 1 = 2`
> - `fact(3) = 3 × 2 = 6` ✅

---

### ⭐ Golden Rule of `return` in Recursion

```
return n * fact(n-1);
```

This line does **3 things in order:**

1. 📞 **Call** `fact(n-1)` → go get the smaller answer
2. ✖️ **Multiply** that answer with `n`
3. 📤 **Return** the final result back up

---

## ❌ Common Mistake — Wrong Use of Function Name

### ✅ Correct Version

```java
return n * fact(n-1);
```

Means: **multiply** `n` with the result of `fact(n-1)`

---

### ❌ Wrong Version

```java
fact(n * fact(n-1));
```

Means: **call `fact()` again** with `n × fact(n-1)` as input — **completely different logic!**

---

### 🔥 Why It's Wrong — Example with n = 5

**✅ Correct:**

```
fact(5)
= 5 × fact(4)
= 5 × 4 × 3 × 2 × 1
= 120 ✅
```

**❌ Wrong:**

```
fact(5 * fact(4))
= fact(5 * 24)
= fact(120)
= 120 × 119 × 118 × ...  ← completely wrong ❌
```

---

### 🧠 Key Difference Table

|Expression|Meaning|Correct?|
|---|---|---|
|`n * fact(n-1)`|Multiply result|✅ Yes|
|`fact(n * fact(n-1))`|Call function again with wrong input|❌ No|

---

## 📞 When Do We Use the Function Name?

> **Simple answer:** We use the function name to **CALL** the function.
> 
> Think of it like: **Function = machine**, **Function name = the ON switch**

---

### 3 Ways Function Names Are Used

#### 1️⃣ Normal Call (just run it)

```java
static void hello() {
    System.out.println("Hello");
}

hello();  // ← function name used to call it
```

#### 2️⃣ Call with Return (store the result)

```java
static int add(int a, int b) {
    return a + b;
}

int result = add(2, 3);  // ← function name used, result stored
```

#### 3️⃣ Recursive Call (function calls itself) 🔥

```java
static int fact(int n) {

    if (n == 1)
        return 1;

    return n * fact(n-1);  // ← function name used inside itself
}
```

Here, `fact(n-1)` means:

> "Call myself again with a smaller problem, get the answer, then use it."

---

### 🎯 Summary Table — When to Use Function Name

|Situation|Example|
|---|---|
|Normal call|`hello();`|
|Store return value|`int x = add(2, 3);`|
|Recursion (self-call)|`fact(n-1)` inside `fact()`|

---

## 🧪 Practice Tests

### Test 1

```
fact(2) = ?

Step-by-step:
2 × fact(1)
= 2 × 1
= ?
```

<details> <summary>Click to reveal answer</summary>

```
fact(2) = 2
```

</details>

---

### Test 2 — Spot the function call

```java
static int square(int n) {
    return n * square(n-1);
}
```

**Which part is the recursive function call?**

- A) `n`
- B) `square(n-1)`
- C) `return`

<details> <summary>Click to reveal answer</summary>

**B) `square(n-1)`**

`square` is the function name. Writing `square(n-1)` calls the function again with a smaller input — that's recursion!

</details>

---

## 📋 Full Summary Cheatsheet

```
┌──────────────────────────────────────────────────────────────┐
│                    RETURN + FUNCTION NAME                    │
├──────────────────────────────────────────────────────────────┤
│  return       → sends value BACK to the caller              │
│  void         → only prints, cannot return a value          │
│  function()   → CALL the function (run it)                  │
│  recursion    → function calling itself by its own name     │
│                                                              │
│  return n * fact(n-1)     ✅ correct                        │
│  fact(n * fact(n-1))      ❌ wrong (calls again with        │
│                               multiplied value)              │
└──────────────────────────────────────────────────────────────┘
```