# 📘 Maven Notes (Placement Preparation)

---

## 🔹 What is Apache Maven?

Maven is a build tool used in Java projects. Its main job is to manage your project completely. It handles dependencies (libraries), compiles code, runs tests, and packages everything into a final runnable file.

> [!tip] Remember This Line Maven is a build tool that combines all the files such as `src`, `static`, `java`, `test`, etc., into a single executable format **(JAR/WAR)**.

---

## 🔹 How Maven Actually Helps You (Real Understanding)

Imagine you are building a project **manually:**

- You download libraries (Spring, Lombok, etc.)
- You add them to the project
- You compile manually
- You create JAR manually

This is difficult and error-prone.

**With Maven:**

- You just write the dependency in one file (`pom.xml`)
- Maven downloads everything automatically
- It builds your project with one command

> [!success] Placement Interview Answer "Maven automates dependency management and project build lifecycle."

---

## 📄 pom.xml — Heart of Maven

This file contains all instructions for Maven.

```xml
<project>
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>hello-world</artifactId>
    <version>0.0.1-SNAPSHOT</version>

    <dependencies>
    </dependencies>
</project>
```

> [!info] Simple Meaning of Each Tag
> 
> - `groupId` → company / package name
> - `artifactId` → project name
> - `version` → version of the project
> - `dependencies` → libraries you want to use

---

## 🔹 Adding a Dependency Using Maven Repository

We use the **Maven Repository** website.

**Step-by-step process:**

1. Open [Maven Repository](https://mvnrepository.com/) website
2. Search for the library (example: Lombok)
3. Click the correct dependency
4. Choose the version
5. Copy the dependency code

**Example (Lombok):**

```xml
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.30</version>
</dependency>
```

6. Paste inside `pom.xml`

---

## ⚠️ Important Issue — Red Error After Pasting

After pasting the dependency, it shows a **red error**.

> [!warning] Why Does This Happen? Maven has **not downloaded** the dependency yet.

> [!success] Fix
> 
> 1. Click **"Sync Maven Changes"** (top/right corner in IntelliJ)
> 2. Maven downloads the library
> 3. Error disappears ✅

---

## 🔧 Lombok Extra Setup

After adding the Lombok dependency:

1. Go to **IntelliJ Settings**
2. Search **Plugins**
3. Install **Lombok plugin**
4. Enable **Annotation Processing**

> [!tip] Then Lombok works properly.

---

## 🔹 Maven Commands (Very Important for Placement)

### 1. Check Maven Version

```bash
./mvnw -version
```

> Shows the Maven version installed.

---

### 2. Clean Project

```bash
./mvnw clean
```

> Deletes old build files (the `target` folder).

---

### 3. Compile Code

```bash
./mvnw compile
```

> Converts Java → bytecode and creates the `target` folder.

---

### 4. Clean + Compile

```bash
./mvnw clean compile
```

> Deletes old files and compiles fresh.

---

### 5. Run Tests

```bash
./mvnw clean test
```

> Runs all test cases.

---

### 6. Verify

```bash
./mvnw verify
```

> Full build check. Creates a snapshot build and checks everything is correct.

---

### 7. Package — Create JAR

```bash
./mvnw clean package
```

> Creates the final **JAR file** (executable).

---

## 🔹 What is the Target Folder?

After a build, your output looks like this:

```
target/
 └── hello-world-0.0.1-SNAPSHOT.jar
```

> [!note] This is your **final application file**.

---

## ▶️ Running the JAR File

**Steps:**

```bash
cd target
java -jar hello-world-0.0.1-SNAPSHOT.jar
```

> [!tip] This runs your Spring Boot application directly from the terminal.

---

## 🔥 Important Understanding (Placement Level)

When you run `./mvnw clean package`, Maven does this internally:

1. Compiles your code
2. Runs all tests
3. Combines everything
4. Creates the JAR

> [!info] That JAR contains:
> 
> - Your code
> - All dependencies
> - Embedded server (Tomcat in Spring Boot)

---

## 🔹 Maven Lifecycle (Real Meaning)

Maven works in **stages** — each command triggers a stage:

```
clean → compile → test → package → verify → install
```

---

## 🧠 Real-Life Analogy

> [!example] Think Like Cooking 🍲
> 
> - **Ingredients** = dependencies
> - **Recipe** = `pom.xml`
> - **Cooking steps** = Maven lifecycle
> - **Final dish** = JAR file

---

## 🔥 Placement-Level Answer

> [!success] If the Interviewer Asks: "What is Maven?" **Say this:**
> 
> "Maven is a build automation and dependency management tool used in Java projects. It uses a `pom.xml` file to manage dependencies and follows a lifecycle to compile, test, and package the application into a deployable JAR or WAR file."

---

## 🧠 Final Understanding

|Without Maven|With Maven|
|---|---|
|You manage everything manually 😓|Maven manages everything automatically 😎|
