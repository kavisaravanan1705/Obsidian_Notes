# 📚 Stack Implementation Using Array (DSA Notes)

---

## 🍽️ Real Life Example of Stack

Think of **plates in a hotel**

You place plates:

- Plate 1
- Plate 2
- Plate 3

Which plate you remove first?

> **Plate 3 (top)**

This is called:

> [!important] LIFO **Last In First Out (LIFO)**

---

## 🏗️ Creating Stack Using Array

Suppose we have:

```java
int arr[5]
```

This means:

```
[ _  _  _  _  _ ]
```

We also need one variable:

```
top
```

This tells where the last element is.

Initially:

```
top = -1
```

> [!note] Means: Stack is **empty**

---

## ➕ Push Operation

### Push 10:

**Step 1:** Increase top:

```
top = top + 1
top = 0
```

**Step 2:** Store value:

```
arr[top] = 10
```

Now:

```
[10 _ _ _ _]
top = 0
```

---

### Push 20:

**Step 1:**

```
top = 1
```

**Step 2:**

```
arr[1] = 20
```

Now:

```
[10 20 _ _ _]
top = 1
```

---

## ➖ Pop Operation

Pop means **remove top**.

Current:

```
[10 20 _ _ _]
top = 1
```

Pop:

Just decrease top:

```
top = top - 1
top = 0
```

Now stack:

```
[10 _ _ _ _]
```

> [!tip] Simple! We don't need to erase 20.

---

## 💡 Basic Stack Code Concept

Forget big code. See only this:

```java
int arr[] = new int[5];
int top = -1;
```

**Push:**

```java
top++;
arr[top] = 10;
```

**Pop:**

```java
top--;
```

**Peek:**

```java
System.out.println(arr[top]);
```

> That is the **whole concept**.

---

## 🖥️ Ultra Simple Full Program

```java
public class Main {

    public static void main(String args[]) {

        int arr[] = new int[5];

        int top = -1;

        top++;
        arr[top] = 10;

        top++;
        arr[top] = 20;

        System.out.println(arr[top]);

        top--;

        System.out.println(arr[top]);

    }
}
```

---

## 🔍 Dry Run

|Step|Action|top|Stack|
|---|---|---|---|
|1|Initial|-1|`[ _ _ _ _ _ ]`|
|2|top++ → arr[0]=10|0|`[10 _ _ _ _]`|
|3|top++ → arr[1]=20|1|`[10 20 _ _ _]`|
|4|Print arr[top]|1|Output: **20**|
|5|top--|0|—|
|6|Print arr[top]|0|Output: **10**|

**Final Output:**

```
20
10
```

---

## ⌨️ Getting Input from User

Simple code with Scanner:

```java
import java.util.*;

public class Main {

    public static void main(String args[]) {

        Scanner sc = new Scanner(System.in);

        System.out.println("Enter stack size:");
        int size = sc.nextInt();

        int arr[] = new int[size];

        int top = -1;

        System.out.println("How many elements to push?");
        int n = sc.nextInt();

        for (int i = 0; i < n; i++) {

            int x = sc.nextInt();

            if (top == size - 1) {
                System.out.println("Stack Full");
                break;
            }

            top++;
            arr[top] = x;

        }

        System.out.println("Top element:");

        if (top != -1) {
            System.out.println(arr[top]);
        }

    }
}
```

---

## ❓ Why We Check: `if(top == size-1)`

Suppose stack size = 5

Array indexes:

```
Index:  0 1 2 3 4
Array: [_ _ _ _ _]
```

Maximum index is:

```
size - 1
5 - 1 = 4
```

So last position = **4**

### If stack is full:

```
Index:  0 1 2 3 4
Array: [10 20 30 40 50]
top = 4
```

Stack is full now.

### If we push again:

Push means:

```
top++
So: top = 5
```

Now we try:

```
arr[5] = value
```

But array only has:

```
0 to 4
```

Index 5 does not exist ❌

This causes:

> [!danger] ArrayIndexOutOfBoundsException Program crashes.

### Prevention:

Use:

```java
if (top == size - 1)
```

Meaning: If top reached last position → **don't push.**

---

## ⭐ Golden Rules

> [!important] Stack Full Condition
> 
> ```
> top == size - 1
> ```

> [!important] Stack Empty Condition
> 
> ```
> top == -1
> ```

---

## 🤔 Why Use `x` Instead of `arr[i]`

### Normal array input:

```java
for (int i = 0; i < n; i++) {
    arr[i] = sc.nextInt();
}
```

This is normal array, **not stack**.

### Stack push method:

Stack only cares about **`top`**

So:

**Step 1:**

```java
int x = sc.nextInt();
```

**Step 2:**

```java
top++;
```

**Step 3:**

```java
arr[top] = x;
```

### Why not `arr[i]`?

Because stack position depends on **`top`**, not loop index.

**Example:**

Suppose `top = 2`

Next push must go to:

```
index 3
```

Not:

```
index i
```

### Both are valid:

**Method 1:**

```java
int x = sc.nextInt();
arr[top] = x;
```

**Method 2:**

```java
arr[top] = sc.nextInt();
```

Both same. ✅

---

## ✅ Corrected Version of Student Code

```java
import java.util.*;

class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.println("Enter the length");
        int n = sc.nextInt();

        int top = -1;

        int arr[] = new int[n];

        System.out.println("Enter elements:");

        for (int i = 0; i < n; i++) {

            if (top == n - 1) {
                System.out.println("Stack is full");
                break;
            }

            top++;

            arr[top] = sc.nextInt();

        }

        if (top != -1) {
            System.out.println("Top element:");
            System.out.println(arr[top]);
        }

    }
}
```

### Mistakes Corrected:

> [!bug] Mistake
> 
> ```java
> if (top == n)
> ```

> [!success] Correct
> 
> ```java
> if (top == n - 1)
> ```

---

> [!bug] Mistake — Check after increment:
> 
> ```java
> top++;
> if (top == n)
> ```

> [!success] Correct — Check before push:
> 
> ```java
> if (top == n - 1)
> top++;
> ```

---

## 🧹 Cleaner Stack Logic

```java
for (int i = 0; i < n; i++) {

    int x = sc.nextInt();

    if (top == n - 1) {
        System.out.println("Stack full");
        break;
    }

    top++;
    arr[top] = x;

}
```

### Better Version:

```java
if (top < n - 1) {
    top++;
    arr[top] = sc.nextInt();
}
```

---

## ⭐ Key Concepts Summary

|Operation|Code|
|---|---|
|Stack follows|**LIFO**|
|Push|`top++` then `arr[top] = value`|
|Pop|`top--`|
|Peek|`arr[top]`|
|Stack full|`top == size - 1`|
|Stack empty|`top == -1`|