# 🔢 Valid Parentheses (LeetCode 20)

---

## 📋 Problem

Given a string containing brackets:

```
() [] {}
```

- Return `true` if brackets are **valid**
- Return `false` if **invalid**

---

## 📌 Examples

### ✅ Valid:

```
()        ✔
()[]{}    ✔
{[]}      ✔
([{}])    ✔
```

### ❌ Invalid:

```
(]        ✘
([)]      ✘
((        ✘
]         ✘
```

---

## 📏 Core Rule

Every opening bracket must have:

- ✅ Correct closing bracket
- ✅ Correct order

**Matching pairs:**

```
( → )
{ → }
[ → ]
```

---

## 🤔 Why Stack is Used

Stack follows:

```
LIFO
Last In First Out
```

**Example — Push:**

```
(
[
{
```

**Stack:**

```
Top → {
       [
       (
```

**When closing comes:**

```
}
```

We check: Top is `{` → Matches → pop

**Stack becomes:**

```
Top → [
       (
```

---

## 💡 Stack Idea

**Rule:**

If opening bracket:

```
push
```

If closing bracket:

```
check top
pop if match
return false if mismatch
```

**At end:**

If stack empty:

```
true
```

Else:

```
false
```

---

## 🔁 Algorithm

Loop through string:

If `( { [` → **Push** into stack.

If `) } ]` → **Check:**

- If stack empty → `return false`
- Else → Pop top. Check:
    
    ```
    ( with ){ with }[ with ]
    ```
    
- If mismatch → `return false`

**After loop:**

Return:

```
stack empty ?
```

---

## 🔍 Dry Run

**Input:**

```
{[]}
```

|Step|Char|Action|Stack|
|---|---|---|---|
|1|`{`|Push|`{`|
|2|`[`|Push|`[ {`|
|3|`]`|Top is `[` → Match → Pop|`{`|
|4|`}`|Top is `{` → Match → Pop|_(empty)_|

**End:** Stack empty →

```
TRUE ✔
```

---

## ☕ Java Code

```java
import java.util.*;

class Solution {

    public boolean isValid(String s) {

        Stack<Character> stack = new Stack<>();

        for (int i = 0; i < s.length(); i++) {

            char c = s.charAt(i);

            if (c == '(' || c == '{' || c == '[') {

                stack.push(c);

            } else {

                if (stack.isEmpty()) {

                    return false;

                }

                char top = stack.pop();

                if (c == ')' && top != '(') {

                    return false;

                }

                if (c == '}' && top != '{') {

                    return false;

                }

                if (c == ']' && top != '[') {

                    return false;

                }

            }

        }

        return stack.isEmpty();

    }

}
```

---

## 🧩 Important Lines Explained

**Create stack:**

```java
Stack<Character> stack = new Stack<>();
```

**Push:**

```java
stack.push(c);
```

**Pop:**

```java
char top = stack.pop();
```

**Check empty:**

```java
stack.isEmpty()
```

**Get character:**

```java
char c = s.charAt(i);
```

---

## 🔎 Meaning of This Line

```java
char top = stack.pop();
```

Means: **Remove top element and store it.**

**Example:**

Stack before:

```
Top → [
       (
```

After `char top = stack.pop();`

Variable:

```
top = '['
```

Stack after:

```
Top → (
```

---

## ❓ Why We Store Pop Value

To check matching:

```java
if (c == ']' && top != '[')
```

We compare **closing bracket** with **opening bracket**.

---

## 🛠️ Important Stack Operations

|Operation|Code|
|---|---|
|Push|`stack.push(x)`|
|Pop|`stack.pop()`|
|Peek|`stack.peek()`|
|Empty check|`stack.isEmpty()`|

---

## ⭐ Interview Pattern Recognition

If question involves:

```
Matching pairs
Balanced symbols
Nearest greater
Previous smaller
Expression evaluation
```

Think:

```
STACK
```

---

## ⏱️ Complexity

**Time Complexity:**

```
O(n)
```

Because we traverse string once.

**Space Complexity:**

```
O(n)
```

Because stack may store all brackets.

---

## ⚠️ Edge Cases

|Input|Output|
|---|---|
|Empty string|`true`|
|Single closing bracket|`false`|
|Only opening brackets|`false`|
|Wrong order|`false`|

---

## 🔧 Small Improvement (Interview Follow Up)

We can also use **HashMap**.

But current solution is **interview safe**. ✅

---

## ⭐ Key Concepts Summary

Stack follows:

```
LIFO
```

|Operation|Code|
|---|---|
|Push|`stack.push()`|
|Pop|`stack.pop()`|
|Peek|`stack.peek()`|
|Empty|`stack.isEmpty()`|

---

## 🏋️ Practice Question

**Input:**

```
([{}])
```

**Output:**

```
true
```

---

## 🧠 Pattern Learned

Stack pattern:

```
Push opening
Pop on closing
Check matching
Return empty stack
```