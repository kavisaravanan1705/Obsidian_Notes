# 🚪 Recent Counter – Queue Problem

**Tags:** #queue #sliding-window #leetcode-933 #java #easy  
**Links:** [[Queue Data Structure]] · [[Sliding Window]] · [[LinkedList vs ArrayDeque]]

---

## 🧠 The Mental Model

> [!info] Security Guard Analogy Imagine you are a **security guard at a gate**.  
> You must count how many people entered in the **last 3000 seconds**.
> 
> - Each time someone arrives → write their time
> - Then erase anyone who came _too long ago_
> - Count whoever remains → that's your answer

---

## ⭐ Core Logic (3 Steps Every Time)

> [!tip] The Algorithm — Memorise This
> 
> ```
> Step 1 → Add new timestamp to queue
> Step 2 → Remove calls where: call_time < t − 3000
> Step 3 → Return queue.size()
> ```

> [!warning] The Removal Rule Remove a call when: `call_time < t − 3000`  
> **Equal is allowed** — boundary calls count! (`<` not `<=`)

---

## 🎬 Step-by-Step Walkthrough

### Step 1 — Start Empty

```
Queue: [ ]
```

---

### Step 2 — `ping(1)`

- Add `1`
- Range: `1 − 3000 = −2999`
- Is `1 < −2999`? → **No** → keep

```
Queue:  [ 1 ]
Answer: 1
```

---

### Step 3 — `ping(100)`

- Add `100`
- Range: `100 − 3000 = −2900`
- Is `1 < −2900`? → **No** → keep both

```
Queue:  [ 1, 100 ]
Answer: 2
```

---

### Step 4 — `ping(3001)`

- Add `3001`
- Range: `3001 − 3000 = 1`
- Is `1 < 1`? → **No** (equal is fine) → keep all

```
Queue:  [ 1, 100, 3001 ]
Answer: 3
```

---

### Step 5 — `ping(3002)` ⚠️ First Removal

- Add `3002`
- Range: `3002 − 3000 = 2`
- Is `1 < 2`? → **YES** → remove ❌
- Is `100 < 2`? → **No** → stop ✅


Before: [ 1,   100, 3001, 3002 ]
        
         removed

After:  [ 100, 3001, 3002 ]
Answer: 3



## 📦 Another Example — `ping(7000)`

**Starting queue:** `[2000, 3000, 4000]`

**Step 1:** Find valid range

```
7000 − 3000 = 4000
Valid calls must be ≥ 4000
```

**Step 2:** Check each element

|Front|Condition|Action|
|---|---|---|
|2000|2000 < 4000? **YES**|Remove ❌|
|3000|3000 < 4000? **YES**|Remove ❌|
|4000|4000 < 4000? **NO**|Stop ✅|

```
Final Queue: [ 4000, 7000 ]
Answer: 2
```

---

## 📊 All Pings at a Glance

|ping(t)|Valid Range|Queue After|Answer|
|---|---|---|---|
|ping(1)|−2999 → 1|[1]|**1**|
|ping(100)|−2900 → 100|[1, 100]|**2**|
|ping(3001)|1 → 3001|[1, 100, 3001]|**3**|
|ping(3002)|2 → 3002|[100, 3001, 3002]|**3**|

---

## 🤔 Why Use a Queue?

> [!info] Queue is Perfect Because...

- 📌 **Old calls always at the front** — calls arrive in increasing time order, so the oldest is always at the head
- 🔁 **FIFO matches the problem** — First In, First Out; first call added is first to expire
- ⚡ **O(1) add & remove** — `LinkedList` gives constant-time operations at both ends
- 🚫 **No searching needed** — we always remove from one end only

```
Structure of queue at any point:

[ oldest → → → → newest ]
  ↑                    ↑
  remove from here     add here
```

---

## 💻 Java Code

```java
import java.util.*;

class RecentCounter {

    Queue<Integer> queue;

    public RecentCounter() {
        queue = new LinkedList<>();
    }

    public int ping(int t) {

        // Step 1: Add new call to the back
        queue.add(t);

        // Step 2: Remove calls that are too old (< t - 3000)
        while (queue.peek() < t - 3000) {
            queue.remove();
        }

        // Step 3: Remaining calls are all within last 3000ms
        return queue.size();
    }
}
```

> [!tip] Key API Methods
> 
> |Method|What it does|
> |---|---|
> |`queue.add(t)`|Insert at **back**|
> |`queue.peek()`|Look at **front** (no remove)|
> |`queue.remove()`|Remove from **front**|
> |`queue.size()`|Count of elements|

---

## 📐 Complexity

|Complexity|Reason|
|---|---|---|
|**Time**|O(1) amortized|Each element added once, removed at most once|
|**Space**|O(W)|W = max calls in any 3000-second window|

---

## 🔁 Quick Recall

> [!abstract] One-Liner to Remember **Add → Prune front (while `front < t−3000`) → Count**  
> Queue works because **old calls always leave from the front**.

---