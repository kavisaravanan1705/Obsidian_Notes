# ⚛️ React JS Notes — Part 2: Development Environment Setup

## 📌 Tags
`#react` `#vscode` `#nodejs` `#npm` `#npx` `#setup` `#extensions` `#javascript` `#frontend`

---

## 1. Setting Up the Development Environment

### 🖥️ Installation of VS Code

- **Easy to use** code editor.
- Comes with **many extensions**.
- Developed by **Microsoft**.
- Built using the **Electron framework**.
- Available for:
  - 🪟 Windows
  - 🐧 Linux
  - 🍎 macOS

---

### 🧩 VS Code Extensions (Installed in Course)

#### 1. ES7+ React/Redux/React-Native Snippets

**Purpose:**
- Provides **ready-made React code snippets**.
- Helps write React components **faster**.
- **Reduces manual typing**.

**Usage Example:**

Shortcut to type:
```
rafce
```

Automatically generates:
```js
import React from 'react'

const App = () => {
  return (
    <div>App</div>
  )
}

export default App
```

**Benefits:**

| ✅ Benefit | Description |
|---|---|
| ⚡ Faster development | No need to manually write boilerplate |
| 📐 Standard React structure | Follows best practices automatically |
| 🛡️ Reduces syntax mistakes | Less chance of typing errors |

---

#### 2. React Native Tools *(Microsoft)*

**Purpose:**
- Helps **debug React applications**.
- Provides **development tools**.
- Helps in running **React Native projects**.

**Benefits:**
- ✅ Easy debugging
- ✅ Better error tracking
- ✅ Development support tools

---

#### 3. Auto Rename Tag

**Purpose:**
- Automatically **renames paired HTML/JSX tags** when one is changed.

**Example:**

Before change:
```html
<div>
</div>
```

If opening tag is changed to `<section>`:
```html
<section>
</div>
```

It **automatically updates** the closing tag:
```html
<section>
</section>
```

**Benefits:**
- ✅ Prevents tag mismatch errors
- ✅ Saves development time
- ✅ Cleaner coding experience

---

#### 4. Auto Close Tag *(Optional)*

**Purpose:**
- Automatically **closes HTML/JSX tags** as you type.

**Example:**

When you type:
```html
<div>
```

It automatically adds:
```html
<div></div>
```

**Benefits:**
- ✅ Faster development
- ✅ Avoids missing closing tags

---

#### 📋 Extensions Quick Reference Table

| # | Extension | Required | Main Use |
|---|---|---|---|
| 1 | ES7+ React/Redux Snippets | ✅ Yes | Code shortcuts & snippets |
| 2 | React Native Tools | ✅ Yes | Debugging & dev tools |
| 3 | Auto Rename Tag | ✅ Yes | Auto-rename paired tags |
| 4 | Auto Close Tag | ⚠️ Optional | Auto-close HTML/JSX tags |

---

## 2. Installation of Node.js

- **Node.js must be installed** before starting React.
- Required to **run React projects**.
- Provides **npm** and **npx**.
- Used to **install React libraries**.

---

## 3. Basic Commands and Concepts

### 📦 What is NPM?

> **NPM = Node Package Manager**

- Comes **bundled with Node.js**.
- Used to **install packages**.
- **Manages dependencies** of a project.
- Used to install **React libraries**.

**Example Commands:**
```bash
npm install
npm start
npm run build
```

---

### ⚡ What is NPX?

> **NPX = Node Package Execute**

- Used to **execute packages without installing them globally**.
- Used to **create React apps quickly**.

**Example Command:**
```bash
npx create-react-app my-app
```

---

### 🔄 Difference Between NPM and NPX

| Feature | NPM | NPX |
|---|---|---|
| Full Form | Node Package Manager | Node Package Execute |
| Purpose | Used to **install** packages | Used to **execute** packages |
| Behaviour | Installs dependencies | Runs package directly |
| Installation needed? | Yes | No |
| Example | `npm install` | `npx create-react-app` |

---

### 📁 What is the CD Command?

> **CD = Change Directory**

- Used to **move between folders** in the terminal.

**Example:**
```bash
cd my-app
```
Moves into the project folder.

---

## 4. Creating Your First React App

### 🚀 Command to Create a React App

```bash
npx create-react-app my-app
```

---

### 🪜 Steps After Running the Command

**Step 1 — Create the project:**
```bash
npx create-react-app my-app
```

**Step 2 — Move into the project folder:**
```bash
cd my-app
```

**Step 3 — Start the application:**
```bash
npm start
```

---

### ✅ Execution Result

After running `npm start`:
- Development server **starts automatically**.
- Browser **opens automatically**.
- **Default React page** appears.
- Terminal shows:
```
webpack compiled successfully
```

> ⚠️ **Note:** You may also see:
> ```
> Note that the development build is not optimized.
> To create a production build, use: npm run build
> ```
> This means the current version is a **development version**. For deployment, use:
> ```bash
> npm run build
> ```

---

## 5. Project Structure Explanation

After creating the project, the folder structure looks like this:

### 📂 node_modules
- Contains all **installed packages**.
- Automatically created.
- ❌ **Do NOT modify this folder.**

---

### 📂 public
- Contains **static files**.
- Most important file: **`index.html`**
  - This is the **main HTML file**.
  - React **injects components** into this file.

---

### 📂 src *(Most Important Folder)*

Contains the **main React code**.

#### 📄 App.js
- The **main component file**.
- All **UI is written here**.

**Example:**
```js
function App() {

  const x = 10;

  return (
    <div>
      {x}
    </div>
  );

}
```

**Important Notes:**
- Code must be written **inside the function**.
- Code must be written **before the return**.
- Variables must be **inside the function**.

To display a variable value in JSX:
```js
const x = 10;  // declare variable
```
```jsx
{x}  // display variable using curly braces
```

> React uses **curly braces `{}`** to show JavaScript values inside JSX.

---

#### 📄 index.js
- **Entry point** of the React app.
- **Connects `App.js` to `index.html`**.

---

#### 📄 App.css
- **Styling file** for the App component.

---

#### 📄 logo.svg
- Default **React logo** file.

---

## 6. Important Coding Rules

### Rule 1 — Code must be inside the function

✅ Correct:
```js
function App() {
  const x = 10;
  return (
    <div>{x}</div>
  );
}
```

❌ Wrong:
```js
const x = 10;  // outside function — NOT allowed
```
Refer the below link
[[Reference image]]

---

### Rule 2 — Variables must be declared before `return`

```js
function App() {
  const x = 10;   // ✅ Before return
  return (
    <div>{x}</div>
  );
}
```

---

### Rule 3 — Use curly braces to display variables

```jsx
{x}
```

---

### Rule 4 — File naming rules *(as told in course)*

| ✅ Correct | ❌ Avoid |
|---|---|
| `myfile.js` | `MyFile.js` |
| `firstapp.js` | `FirstApp.js` |

> 📝 **Note:** React components usually use capital letters, but follow your course instructor's rule as a beginner.

---

## 7. Getting Started with React JS

### 🛤️ Steps to Begin Learning React (in order)

1. Create a new project
2. Understand the folder structure
3. Learn **components**
4. Learn **JSX**
5. Learn **props**
6. Learn **state**

---

## 8. Quick Summary

### ⚡ React Setup Flow

```
Step 1 → npx create-react-app my-app   (Create project)
Step 2 → cd my-app                      (Enter project folder)
Step 3 → npm start                      (Run project)
```

---

### 🧠 Key Concepts Learned

- ✅ React basics
- ✅ NPM
- ✅ NPX
- ✅ CD command
- ✅ Project structure
- ✅ First app execution
- ✅ VS Code setup
- ✅ File structure
- ✅ Variable rendering with `{}`
- ✅ JSX basics

---

### 💡 Why Extensions Are Important

Extensions help with:
- ⚡ Faster coding
- 🛡️ Error reduction
- 📈 Better productivity
- 💬 Code suggestions
- 🐛 Debugging support

---

Props and components
props stands for properties
to use components , just call the componenst inside the component
when we want same variable in differeent component (To reuse the same variable in differesnt components) , in that time we use props
to use props Syntax is :
props.variable name 
