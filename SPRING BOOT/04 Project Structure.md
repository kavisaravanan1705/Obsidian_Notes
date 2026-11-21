
# 📘 Spring Boot Project Structure

---

> [!tip] Think of It Like a School 🏫 Your project is like a school building — each folder is one room with a specific job.

---

## 🗂️ Full Structure

```
project/
 └── src/
     └── main/
         ├── java/
         └── resources/
 └── test/
 └── pom.xml
```

---

## 🔹 1. `src/` — Main Folder

> [!note] Meaning All your code lives here.

> 📦 Think: Big box → everything is inside it

---

## 🔹 2. `main/` — Real App Code

> [!note] Meaning Contains the actual application — the important code that runs.

---

## 🔹 3. `java/` — Brain 🧠 of the App

**Path:** `src/main/java/`

> [!note] Meaning This is where you write all your Java code.

**Inside this folder:**

```
com.example.project/
 ├── App.java
 ├── controller/
 ├── service/
 └── repository/
```

---

### 🔸 (a) Main Class — App.java 🚀

```java
@SpringBootApplication
public class App {
    public static void main(String[] args) {
        SpringApplication.run(App.class, args);
    }
}
```

> [!tip] Meaning This class **starts your entire app**.

---

### 🔸 (b) `controller/` 🎮

> [!note] Meaning Handles requests coming from the user (browser / Postman).

```java
@RestController
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello";
    }
}
```

> [!example] Flow User → `/hello` → Controller responds

---

### 🔸 (c) `service/` ⚙️

> [!note] Meaning Contains the **business logic** of your app.

```java
@Service
public class HelloService {

    public String getMessage() {
        return "Hello from service";
    }
}
```

> [!tip] Controller calls Service to process the logic.

---

### 🔸 (d) `repository/` 💾

> [!note] Meaning Talks directly to the **database**.

```java
@Repository
public interface UserRepo {
}
```

> [!tip] Used to store and retrieve data from the database.

---

## 🔹 4. `resources/` — Settings + Extra Files

**Path:** `src/main/resources/`

---

### 🔸 (a) `application.properties`

> [!note] Meaning Settings / configuration of your app.

```properties
server.port=8081
```

> Changes the server port.

---

### 🔸 (b) `static/`

> [!note] Meaning Frontend files go here:
> 
> - HTML
> - CSS
> - JS

---

### 🔸 (c) `templates/`

> [!note] Used For Dynamic HTML pages using **Thymeleaf**.

---

## 🔹 5. `test/`

> [!note] Meaning Used for writing and running test cases.

> [!tip] Beginners can ignore this for now.

---

## 🔹 6. `pom.xml` 📄 — VERY IMPORTANT

> [!abstract] Meaning This is the **project manager** — it adds libraries and manages versions.

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

> [!info] This dependency gives you:
> 
> - REST API support
> - Embedded server (Tomcat)

---

## 🧠 Complete Flow (Super Easy)

```
👤 User  →  /hello
              ↓
         🎮 Controller
              ↓
          ⚙️ Service
              ↓
        💾 Repository (DB)
              ↓
          ⬆ Response back to User
```

---

## 🔥 One-Line Memory

> [!abstract] Quick Reference
> 
> - `java/` → your code
> - `controller/` → handle requests
> - `service/` → business logic
> - `repository/` → database access
> - `resources/` → settings & config
> - `pom.xml` → dependencies

---

## 🧠 Baby Summary

> [!tip] **Spring Boot project =** 📦 Code + ⚙️ Logic + 💾 Data + ⚡ Settings

---

---

# 🍔 Real-Life Example — Zomato Flow

---

> [!example] Story You open Zomato and search: **"Pizza"** Here's what happens inside Spring Boot:

1. You (user) send a request 📱
2. Goes to **Controller** 🎮
3. Controller asks **Service** ⚙️
4. Service checks **Repository** 💾
5. Repository gets data from **Database** 🗄️
6. Response comes back 🍕

---

## 📊 Full Diagram

```
👤 User (Zomato App)
        ↓
🎮 Controller   ← receives request "/search"
        ↓
⚙️ Service      ← process logic: find pizza
        ↓
💾 Repository   ← fetch from database
        ↓
🗄️ Database     ← stores restaurant data
        ↑
💾 Repository
        ↑
⚙️ Service
        ↑
🎮 Controller
        ↑
📱 User gets result (Pizza list 🍕)
```

---

## 🔍 Mapped to Spring Boot Structure

|Real Life|Spring Boot Folder|
|---|---|
|App request|`controller/`|
|Business logic|`service/`|
|Data access|`repository/`|
|App settings|`resources/`|

---

## 💻 Code Example — Zomato Style

### 🎮 Controller

```java
@RestController
public class FoodController {

    @Autowired
    FoodService service;

    @GetMapping("/food")
    public String getFood() {
        return service.getFood();
    }
}
```

---

### ⚙️ Service

```java
@Service
public class FoodService {

    @Autowired
    FoodRepository repo;

    public String getFood() {
        return repo.getFoodData();
    }
}
```

---

### 💾 Repository

```java
@Repository
public class FoodRepository {

    public String getFoodData() {
        return "Pizza 🍕 available!";
    }
}
```

---

## 🧠 Super Simple Flow

> [!abstract] **User → Controller → Service → Repository → Data → Back to User**

---

## 🔥 Instagram Example (1 Line)

> [!example] Open Instagram Feed
> 
> - **Controller** → receives the request
> - **Service** → decides what posts to show
> - **Repository** → fetches posts from the database

---

## 🧠 Final Memory Trick

> [!tip] Remember It Like a Restaurant 🍽️
> 
> - 🎮 **Controller** = "Take the order"
> - ⚙️ **Service** = "Cook the food"
> - 💾 **Repository** = "Get the ingredients"