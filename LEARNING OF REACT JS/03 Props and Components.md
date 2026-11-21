# ⚛️ React JS Notes — Part 3: Components and Props

## 📌 Tags

`#react` `#components` `#props` `#jsx` `#functional-component` `#class-component` `#javascript` `#frontend`

---

## 1. React Components

### 🧩 What is a Component?

- A component is a **reusable piece of UI** in React.
- Each part of the UI can be a **separate component**.

**Examples of components:**

|Component|Role|
|---|---|
|`Navbar`|Top navigation bar|
|`Button`|Clickable button|
|`Card`|Info display card|
|`Footer`|Bottom section|

---

### 🔀 Types of Components

#### 1. ✅ Functional Component _(Most Important — Modern React)_

- Simple **JavaScript function**.
- **Returns JSX**.
- **Modern React uses functional components**.

**Standard function version:**

```js
function App() {
  return (
    <div>Hello React</div>
  );
}

export default App;
```

**Arrow function version:**

```js
const App = () => {
  return (
    <div>Hello React</div>
  );
}
```

---

#### 2. 🏛️ Class Component _(Less Used Now)_

- Uses **ES6 classes**.
- Requires a **`render()` method**.
- Mostly **replaced by functional components**.

**Example:**

```js
import React, { Component } from "react";

class App extends Component {
  render() {
    return (
      <div>Hello React</div>
    );
  }
}

export default App;
```

---

#### 📋 Functional vs Class Component — Quick Comparison

|Feature|Functional Component|Class Component|
|---|---|---|
|Syntax|JavaScript function|ES6 Class|
|`render()` needed?|❌ No|✅ Yes|
|Modern usage|✅ Preferred|❌ Less used|
|Hooks support|✅ Yes|❌ No|

---

### 🔠 Component Naming Rules _(Important)_

> ⚠️ **React treats lowercase names as HTML tags — always use Capital letters for components!**

**Rules:**

- Component name **must start with a capital letter**.
- File name is **usually the same as the component name**.

|✅ Correct|❌ Wrong|
|---|---|
|`App.js`|`app.js`|
|`Navbar.js`|`navbar.js`|
|`Student.js`|`student.js`|

**Reason:** React treats lowercase tags as **HTML elements**, not components.

---

### 🛠️ Creating a Component

**`Student.js` — creating the component:**

```js
function Student() {
  return (
    <h1>Student Component</h1>
  );
}

export default Student;
```

**`App.js` — using the component:**

```js
import Student from "./Student";

function App() {
  return (
    <div>
      <Student/>
    </div>
  );
}
```

---

### 📏 Rules of Components

#### Rule 1 — Must return only ONE parent element

❌ Wrong:

```jsx
return (
  <h1>Hello</h1>
  <p>React</p>
)
```

✅ Correct:

```jsx
return (
  <div>
    <h1>Hello</h1>
    <p>React</p>
  </div>
)
```

---

#### Rule 2 — Use Fragment if no extra `<div>` is needed

```jsx
return (
  <>
    <h1>Hello</h1>
    <p>React</p>
  </>
)
```

> 💡 `<>...</>` is shorthand for `<React.Fragment>...</React.Fragment>`. It groups elements without adding an extra DOM node.

---

## 2. Props in React

### 📦 What are Props?

> **Props = Properties**

Props are used to:

- **Pass data** from parent to child component.
- Make components **dynamic**.
- **Reuse components** with different data.

---

### 🔁 Props Flow Direction _(Very Important)_

```
✅  Parent  →  Child   (Correct)
❌  Child   →  Parent  (NOT possible with props)
```

> Props always flow **downward — from Parent to Child only**.

---

### ✏️ Creating Props — Basic Example

**Parent component (sending data):**

```jsx
<Student name="Kavi"/>
```

**Child component (receiving data):**

```js
function Student(props) {
  return (
    <h1>{props.name}</h1>
  );
}
```

**Output:**

```
Kavi
```

---

### ✂️ Props Using Destructuring _(Important — Industry Practice)_

Instead of:

```js
function Student(props) {
  return <h1>{props.name}</h1>
}
```

Use destructuring:

```js
function Student({ name }) {
  return <h1>{name}</h1>
}
```

**Why use destructuring?**

- ✅ Cleaner code
- ✅ Industry standard practice
- ✅ Easier to read and maintain

---

### 📨 Multiple Props Example

**Parent (sending multiple props):**

```jsx
<Student name="Kavi" age="19" dept="CSE"/>
```

**Child — standard way:**

```js
function Student(props) {
  return (
    <div>
      <h1>{props.name}</h1>
      <h2>{props.age}</h2>
      <h3>{props.dept}</h3>
    </div>
  );
}
```

**Child — with destructuring (better version):**

```js
function Student({ name, age, dept }) {
  return (
    <div>
      <h1>{name}</h1>
      <h2>{age}</h2>
      <h3>{dept}</h3>
    </div>
  );
}
```

---

### 📌 Important Props Rules

#### Rule 1 — Props are Read-Only

❌ Wrong:

```js
props.name = "Raj";  // Cannot modify props
```

> Props **cannot be modified** inside the child component.

---

#### Rule 2 — Props are Immutable

> **Immutable** means the value **cannot be changed** inside the child component.

---

#### Rule 3 — Props can pass different data types

|Data Type|Example|
|---|---|
|String|`name="Kavi"`|
|Number|`marks={95}`|
|Array|`list={[1,2,3]}`|
|Object|`info={{id:1}}`|
|Function|`fun={greet}`|

---

### 🔢 Passing Number Props

```jsx
<Student marks={95}/>
```

> 📝 **Note:**
> 
> - Numbers → use `{}`
> - Strings → use `" "`

---

### 🔧 Passing Function as Props _(Important Interview Concept)_

**Parent component:**

```js
function App() {

  function greet() {
    alert("Hello");
  }

  return (
    <Student fun={greet}/>
  );
}
```

**Child component:**

```js
function Student(props) {
  return (
    <button onClick={props.fun}>
      Click
    </button>
  );
}
```

---

### 🛡️ Default Props

Used when **no value is passed** from the parent.

```js
function Student({ name = "Guest" }) {
  return <h1>{name}</h1>
}
```

> If no `name` prop is passed, it defaults to `"Guest"`.

---

### ⚖️ Props vs State _(Basic Difference)_

|Feature|Props|State|
|---|---|---|
|Source|Passed from **parent**|Managed **inside** component|
|Modifiable?|❌ Read-only|✅ Can change|
|Mutability|Immutable|Mutable|
|Purpose|Communication between components|Managing internal data|

---

## 3. ⚡ Must Know Interview Points

> 🎯 **Very important — memorize these!**

- ✅ Components are **reusable**.
- ✅ Props **pass data** from parent to child.
- ✅ Props are **read-only**.
- ✅ Props flow **parent → child** only.
- ✅ Component names **must start with a capital letter**.
- ✅ Must return a **single parent element**.
- ✅ Use `{}` to **display variables** in JSX.

---

## 4. ❌ Common Beginner Mistakes

### Mistake 1 — Not using a capital letter for component name

```js
student()  // ❌ Wrong
Student()  // ✅ Correct
```

---

### Mistake 2 — Returning multiple elements without a parent wrapper

```jsx
// ❌ Wrong
<h1></h1>
<p></p>

// ✅ Correct — wrap in a parent or Fragment
<>
  <h1></h1>
  <p></p>
</>
```

---

### Mistake 3 — Using component without importing it

```jsx
// ❌ Wrong — using without import
<Student/>
```

```js
// ✅ Correct — always import first
import Student from "./Student";
```

---

## 5. 🗺️ Quick Visual Summary

```
App.js (Parent)
│
├── <Student name="Kavi" age="19" dept="CSE"/>
│         │
│         ▼
│   Student.js (Child)
│   receives → props.name / props.age / props.dept
│   displays → Kavi / 19 / CSE
│
└── Props flow: Parent → Child only ✅
```

---

