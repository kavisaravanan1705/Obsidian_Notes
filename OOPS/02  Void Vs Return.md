# ☕ Java Notes — `void` vs `return` : Real Life Examples

## 📌 Tags
`#java` `#void` `#return` `#methods` `#real-life-examples` `#basics` `#placement`

---

> 🧠 SUPER EASY MEMORY TRICK
> | Keyword | Think of it as |
> |---|---|
> | `void` | **"Just do"** — work is done, nothing given back |
> | `return` | **"Give answer"** — result is sent back to caller |

---

## 🎯 Real Life Example 1 — Tea Shop ☕

### Case 1 — `void` (No Return)

> 👉 You ask the shopkeeper: **"Anna, tea kudunga"**

He:
- Makes tea 🍵
- Gives it directly to you
- Does **not give any value back** (no number, no info)

```java
void makeTea() {
    System.out.println("Tea is ready");
}
```

> 🧠 **Meaning:** Work is done, just output → use `void`

---

### Case 2 — `return` (Gives Back a Value)

> 👉 You ask: **"Anna, bill evlo?"**

He:
- Calculates 🧮
- Gives you the answer: **₹15**

```java
int getBill() {
    return 15;
}
```

> 🧠 **Meaning:** You need an answer → use `return`

---

### 📊 Tea Shop Summary

| Situation | What Happens | Method Type |
|---|---|---|
| "Anna, tea kudunga" | Tea made & given — no value returned | `void` |
| "Anna, bill evlo?" | Answer (₹15) returned to you | `return` |

---

## 🎯 Real Life Example 2 — College Marks 🎓

### Case 1 — `void` (Just Showing)

> 👉 Teacher says: **"I will just announce your mark"**

```java
void showMark() {
    System.out.println(85);
}
```

> 🧠 **Just showing the mark** → no value needed back → `void`

---

### Case 2 — `return` (Value Needed Later)

> 👉 You calculate total marks **to use for percentage later**

```java
int totalMarks(int m1, int m2) {
    return m1 + m2;
}
```

```java
int total = totalMarks(80, 90);  // value stored for later use
```

> 🧠 **You need that value later** → use `return`

---

### 📊 College Marks Summary

| Situation | What Happens | Method Type |
|---|---|---|
| Teacher announces mark | Just displayed, not stored | `void` |
| Calculate total for percentage | Result stored and used later | `return` |

---

## 🎯 Real Life Example 3 — Mobile Recharge 📱

### Case 1 — `void` (Just a Message)

> 👉 You recharge → just get a success message

```java
void recharge() {
    System.out.println("Recharge successful");
}
```

> 🧠 Just doing the task, no value needed back → `void`

---

### Case 2 — `return` (Value Needed)

> 👉 You check your current balance

```java
int checkBalance() {
    return 120;
}
```

```java
int balance = checkBalance();  // balance = 120, stored for use
```

> 🧠 You need the balance value to use it → `return`

---

### 📊 Mobile Recharge Summary

| Situation | What Happens | Method Type |
|---|---|---|
| Recharge done | Success message shown, nothing returned | `void` |
| Check balance | Balance value (120) returned and stored | `return` |

---

## 🔥 All 3 Examples — Master Comparison Table

| Example | `void` Case | `return` Case |
|---|---|---|
| ☕ Tea Shop | Make & give tea directly | Give bill amount (₹15) |
| 🎓 College Marks | Announce mark on board | Calculate total for percentage |
| 📱 Mobile Recharge | Show "Recharge successful" | Return balance (120) |

---

## 🔥 Final Simple Rule

> ### 👉 If **result is needed** → use `return`
> ### 👉 If **just doing a task** → use `void`

---

## 🧠 Decision Flow — Which One to Use?

```
Do you need the result of this method later?
             │
      ┌──────┴──────┐
     YES            NO
      │              │
  use return      use void
      │              │
 int getBill()   void makeTea()
 return 15;      System.out.println(...)
```

---
