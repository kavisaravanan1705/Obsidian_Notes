# 🔄 Implement Queue Using Stacks

**Tags:** #stack #queue #leetcode-232 #java #easy  

---

## 💡 The Core Idea

> [!info] Two-Stack Trick Use **two stacks** with different roles:
> 
> |Stack|Role|
> |---|---|
> |`s1`|**Push** — receives all new elements|
> |`s2`|**Pop / Peek** — serves elements in correct order|
> 
> **Why two?** Stack is LIFO. Queue is FIFO.  
> Pushing into a second stack **reverses the order** — turning LIFO into FIFO. 🔁

```
FIFO  →  needs order:  1, 2, 3  (oldest first)
LIFO  →  gives order:  3, 2, 1  (newest first)

Reverse LIFO  =  FIFO  ✅
```

---

## ⚙️ Working Principle

### 📥 Push Operation

> Simply push into `s1`. Nothing special.

```
push(1) → push(2) → push(3)

s1 = [ 1, 2, 3 ]   ← top is 3
s2 = [ ]
```

> [!tip] Time Complexity: **O(1)**

---

### 📤 Pop Operation

**If `s2` is empty** → move everything from `s1` to `s2` first.  
Then pop from `s2`.

```
Step 1 — Transfer s1 → s2:

s1 = [ 1, 2, 3 ]        s2 = [ ]
          ↓ pop & push ↓
s1 = [ ]                 s2 = [ 3, 2, 1 ]
                                        ↑ top is 1  ✅

Step 2 — Pop from s2:

pop() → 1   (correct FIFO order!)
```

> [!tip] Time Complexity: **O(1) amortized**  
> Each element is moved at most once across its entire lifetime.

---

### 👀 Peek Operation

Same logic as pop — but **don't remove**, just look at the top of `s2`.

```
peek() → s2.peek()   (returns front without removing)
```

---

### ❓ Empty Check

Queue is empty only when **both** stacks are empty.

```
empty() → s1.isEmpty() && s2.isEmpty()
```

---

## 🧠 Why IF — Why WHILE

### Why `if (s2.isEmpty())`?

> [!warning] Transfer ONLY When Needed
> 
> - `s2` already holds elements **in the correct order** from a previous transfer
> - Transferring again would **destroy** that order
> - We transfer only when `s2` runs out

```
❌ Transfer every time:

push(1), push(2)
pop() → transfer → s2 = [2,1] → pop 1 ✅
push(3)
pop() → transfer again → s2 = [3,2] → pop 2 ❌ (wrong!)

✅ Transfer only when s2 is empty:

pop() → s2 still has [2] → pop 2 ✅
```

---

### Why `while (!s1.isEmpty())`?

> [!warning] Move ALL Elements — Never Partial Partial transfer breaks FIFO order completely.

```
❌ Partial transfer (wrong):

s1 = [ 1, 2, 3 ]
Move only 3 →  s2 = [ 3 ]

pop() → 3   ← WRONG (should be 1)

✅ Full transfer (correct):

s1 = [ 1, 2, 3 ]
Move all  →  s2 = [ 3, 2, 1 ]

pop() → 1   ← CORRECT ✅
```

---

## 💻 Java Code

```java
import java.util.*;

class MyQueue {

    Stack<Integer> s1 = new Stack<>();  // for push
    Stack<Integer> s2 = new Stack<>();  // for pop/peek

    // O(1) — just push to s1
    public void push(int x) {
        s1.push(x);
    }

    // O(1) amortized — transfer only when s2 is empty
    public int pop() {
        if (s2.isEmpty()) {
            while (!s1.isEmpty()) {
                s2.push(s1.pop());
            }
        }
        return s2.pop();
    }

    // Same as pop but don't remove
    public int peek() {
        if (s2.isEmpty()) {
            while (!s1.isEmpty()) {
                s2.push(s1.pop());
            }
        }
        return s2.peek();
    }

    // Empty only when both stacks are empty
    public boolean empty() {
        return s1.isEmpty() && s2.isEmpty();
    }
}
```

---

## 📊 Time Complexity

|Operation|Complexity|Reason|
|---|---|---|
|`push`|O(1)|Direct push to s1|
|`pop`|O(1) amortized|Each element moved at most once|
|`peek`|O(1) amortized|Same as pop logic|
|`empty`|O(1)|Just two isEmpty checks|

> [!abstract] What is Amortized O(1)? One single `pop` can cost O(n) if it triggers a transfer.  
> But across **n operations**, total work is O(n) → **O(1) per operation on average**.  
> Think of it as: each element pays for its own move — once.

---

## 🗺️ Visual Flow

```
push(1), push(2), push(3)
         │
         ▼
   s1 = [1, 2, 3]     s2 = []

pop() called → s2 is empty → TRANSFER
         │
         ▼
   s1 = []     s2 = [3, 2, 1]
                          ↑ top
pop() → returns 1  ✅

push(4) → s1 = [4]   s2 = [3, 2]

pop() → s2 not empty → returns 2  ✅  (no transfer needed)
```

---

## 🧩 Memory Trick

> [!tip] Remember It Like This
> 
> ```
> PUSH  →  always goes to s1
> 
> POP / PEEK:
>   if s2 is empty:
>       move everything from s1 → s2
>   then use s2
> ```
> 
> **s1 = inbox    s2 = outbox**  
> Only restock the outbox when it's completely empty.

---

## 🔑 Key Interview Points

> [!abstract] Say These Out Loud in an Interview
> 
> 1. Use **two stacks** — one for input, one for output
> 2. Transfer from `s1 → s2` **only when `s2` is empty**
> 3. Always transfer **all** elements (not partial)
> 4. This gives **amortized O(1)** for all operations
> 5. Each element is pushed and popped at most **twice total**

---

## 🔍 Pattern Recognition

Use this pattern when the problem mentions:

- _"Implement queue using stack(s)"_
- _"Simulate FIFO using LIFO"_
- _"Reverse order using stacks"_
- _"Stack-based queue / queue-based stack"_

---