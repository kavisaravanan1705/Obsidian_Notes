# 📘 Spring Boot Notes – Part 2

### 1. `@SpringBootApplication`

Combination of **3 annotations**:

- `@Configuration`
- `@EnableAutoConfiguration`
- `@ComponentScan`

> [!tip] Meaning "Start and configure everything automatically"
---




## 🔹 Core Annotations

### 1. `@Configuration`

> [!note] Definition Used to define a class that contains bean methods. Spring uses this class to create and manage objects (beans).

> [!tip] Simple Meaning This class tells Spring: **"I will create objects here"**

```java
@Configuration
public class AppConfig {

    @Bean
    public String message() {
        return "Hello Spring";
    }
}
```

> [!info] Explanation
> 
> - `@Configuration` → marks the class as a config class
> - `@Bean` → tells Spring to create the object
> - Spring stores it and reuses it wherever needed

---

### 2. `@EnableAutoConfiguration`

> [!note] Definition Tells Spring Boot to automatically configure the application based on the dependencies added.

> [!tip] Simple Meaning Spring Boot automatically sets everything up — server, database, etc.

```java
@EnableAutoConfiguration
public class MyApp {
    public static void main(String[] args) {
        SpringApplication.run(MyApp.class, args);
    }
}
```

> [!info] Explanation
> 
> - If you add the web dependency → Spring sets up the server automatically
> - No manual setup needed at all

---

### 3. `@ComponentScan`

> [!note] Definition Tells Spring to scan packages and find components — classes marked with annotations.

> [!tip] Simple Meaning Spring searches and finds your classes automatically

```java
@ComponentScan("com.example")
public class AppConfig {
}
```

> [!info] Explanation Spring scans the `com.example` package and finds classes annotated with:
> 
> - `@Component`
> - `@Service`
> - `@Repository`
> - `@Controller`

---

### 🔥 Important Note

> [!abstract] Key Formula `@SpringBootApplication` = `@Configuration` + `@EnableAutoConfiguration` + `@ComponentScan`

---

## 🧠 Annotations — Super Simple Mental Models

> [!tip] One Idea to Remember First **Spring's job = Create objects + give them where needed**
> 
> Instead of you writing `Car car = new Car();` → Spring does it for you automatically.

---

### `@Configuration` — Think of a Kitchen

> 🏠 You are building a house → `@Configuration` = the kitchen where things are prepared

- A class where objects (beans) are created and handed to Spring

```java
@Configuration
public class AppConfig {

    @Bean
    public Car car() {
        return new Car();
    }
}
```

> [!example] Simple Flow You told Spring → "Create a Car" → Spring stores it → gives it wherever needed

---

### `@EnableAutoConfiguration` — Think of a Hotel Room

> 🏨 You enter the hotel → everything is already ready (bed, AC, lights)

- Spring automatically sets things up based on what you've added

> [!example] Example You add Spring Web → Spring automatically starts the server. You never wrote `startServer();` — it still works!

---

### `@ComponentScan` — Think of Attendance

> 👀 Teacher checking attendance in a classroom

- Spring goes into the package you specify and finds all annotated classes

```java
@ComponentScan("com.example")
```

> Spring finds: `@Component`, `@Service`, `@Controller`

---

### 🔥 Final Easy Lines

|Annotation|What it does|
|---|---|
|`@Configuration`|I will create objects|
|`@EnableAutoConfiguration`|Spring sets everything up automatically|
|`@ComponentScan`|Spring finds and registers classes|

---

## ⚙️ Setup Notes

### 1. Install Java JDK

> [!note] What is it? Needed to run Java programs on your machine.

**Recommended:** JDK 17 or above

**Steps:**

1. Download from Oracle JDK or OpenJDK
2. Install normally
3. Set environment variable:

```
JAVA_HOME = C:\Program Files\Java\jdk-17
```

4. Verify installation:

```bash
java -version
```

---

### 2. Install IntelliJ IDEA

> [!note] What is it? The best IDE for writing Spring Boot code — gives auto-suggestions and easy project setup.

**Steps:**

1. Go to the official JetBrains website
2. Download **Community Edition** (free)
3. Install normally
4. Open IntelliJ and start coding

> [!tip] Why IntelliJ?
> 
> - Auto-suggestions while typing
> - Shows errors instantly
> - Runs your program with one click

---

### 3. Create a Spring Boot Project

> [!tip] Easiest Way — Use Spring Initializr

**Steps:**

1. Go to [start.spring.io](https://start.spring.io/)
2. Choose:
    - **Project:** Maven
    - **Language:** Java
    - **Spring Boot version:** latest stable
3. Add dependency: **Spring Web**
4. Click **Generate**
5. Extract the zip and open in IntelliJ (file folder not compressed file)

---

### 4. Install Postman

> [!note] What is it? A tool to test your APIs without needing a frontend.

**Steps:**

1. Download Postman from the official site
2. Install and open the app

> [!example] Example Usage
> 
> - URL: `http://localhost:8080/hello`
> - Method: `GET`
> - Click **Send** → Response appears

---

## 🧠 Quick Revision — Exam Ready

> [!abstract] Ultra Short Summary (2 lines)
> 
> - `@Configuration` → creates objects (beans)
> - `@EnableAutoConfiguration` → automatic setup based on dependencies
> - `@ComponentScan` → scans and finds annotated classes

| Tool              | Purpose                          |
| ----------------- | -------------------------------- |
| **JDK**           | Required to run Java             |
| **IntelliJ IDEA** | IDE for writing and running code |
| **Postman**       | Tool to test APIs                |
|                   |                                  |
# HelloSpringBootController

> **Package:** `dev.codeio.HelloSpringBoot`  
> **Type:** REST Controller  
> **Framework:** Spring Boot

---

## 📄 Source Code [HelloSpringBootController]

```java
package dev.codeio.HelloSpringBoot;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloSpringBootController {
    @GetMapping("/todo")
    public String func(){
        return "kavi";
    }
}
```

---

## 🧩 Annotations

|Annotation|Description|
|---|---|
|`@RestController`|Marks class as REST controller; returns data directly to HTTP response|
|`@GetMapping("/todo")`|Maps HTTP GET requests on `/todo` to `func()`|

---

## 🔁 Endpoint

|Method|Path|Returns|
|---|---|---|
|`GET`|`/todo`|`"kavi"` (plain string)|

---

## 🧪 How to Test

```bash
curl http://localhost:8080/todo
# Response: kavi
```

Or open in browser:

```
http://localhost:8080/todo
```

---

## 💡 Improvement Suggestions

### 1. Better Method Name

```java
// ❌ Too generic
String func()

// ✅ Descriptive
public String getTodo()
```

### 2. Use `ResponseEntity` for Proper HTTP Response

```java
@GetMapping("/todo")
public ResponseEntity<String> getTodo() {
    return ResponseEntity.ok("kavi");
}
```

### 3. Add Class-Level `@RequestMapping`

```java
@RestController
@RequestMapping("/api")
public class HelloSpringBootController {
    @GetMapping("/todo")
    public String getTodo() {
        return "kavi";
    }
}
```

> Endpoint becomes: `http://localhost:8080/api/todo`

---

## 🔗 Related

- [[Spring Boot Setup]]
- [[REST Controller Basics]]
- [[Spring Annotations]]

---
