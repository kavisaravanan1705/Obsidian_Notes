
# 📘 Spring Boot Notes – Part 1 (Basics)

---

## 🔹 What is Spring Boot?

- Spring Boot is a Java framework used to build web applications easily.
- It reduces manual configuration.
- You can create apps quickly with less code.

> [!note] Simple Meaning **Spring Boot = Fast way to build Java backend applications**

---

## 🔹 Why Use Spring Boot?

- No need to configure everything manually
- Built-in server (no need to install separately)
- Easy to create REST APIs
- Production-ready features

> [!example] Example Instead of writing 100 lines of config → Spring Boot does it in **1–2 lines**

---

## 🔹 Main Features

|Feature|Description|
|---|---|
|**Auto Configuration**|Automatically sets up the project|
|**Standalone Application**|Runs on its own|
|**Embedded Server**|Uses Apache Tomcat|
|**Starter Dependencies**|Predefined libraries|

---

## 🔹 Project Structure

```
src/
 └── main/
     ├── java/
     │    └── com.example.project/
     │          └── MainApplication.java
     └── resources/
          ├── application.properties
          └── static/
```

---

## 🔹 Main Class (Entry Point)

```java
@SpringBootApplication
public class MainApplication {
    public static void main(String[] args) {
        SpringApplication.run(MainApplication.class, args);
    }
}
```

> [!info] Explanation
> 
> - `@SpringBootApplication` → Starts everything
> - `main()` → Entry point of the program
> - `SpringApplication.run()` → Runs the app

> [!tip] Simple Meaning This class starts your **entire** Spring Boot application.

---

## 🔹 Important Annotations

### 1. `@SpringBootApplication`

Combination of **3 annotations**:

- `@Configuration`
- `@EnableAutoConfiguration`
- `@ComponentScan`

> [!tip] Meaning "Start and configure everything automatically"

---

### 2. `@RestController`

Used to create REST APIs.

```java
@RestController
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello World";
    }
}
```

> [!success] Browser Output `http://localhost:8080/hello` → `Hello World`

---

### 3. `@GetMapping`

Handles **GET** requests.

> [!example] Example Open a URL → You get data back

---

## 🔹 What is a REST API?

- REST API allows **frontend ↔ backend** communication
- Uses HTTP methods:

|Method|Action|
|---|---|
|`GET`|Read data|
|`POST`|Create data|
|`PUT`|Update data|
|`DELETE`|Remove data|

> [!example] Real-World Example Instagram loading posts → uses APIs in the background

---

## 🔹 application.properties

Used to configure app settings.

```properties
server.port=8081
```

> [!info] Effect Changes server port from **8080 → 8081**

---

## 🔹 How Spring Boot Runs

1. You run the main class
2. Spring Boot starts
3. Embedded server starts
4. Your APIs become available

> [!tip] Simple Flow `Run` → `Server Start` → `API Ready`

---

## 🔹 Advantages (Exam Points)

- ✅ Fast development
- ✅ Less configuration
- ✅ Easy to learn
- ✅ Microservices friendly

---

## 🧠 Quick Revision (2 lines)

> [!abstract] Summary
> 
> - Spring Boot is a Java framework to build apps quickly.
> - It provides **auto configuration** + **embedded server** + **REST API support**.
