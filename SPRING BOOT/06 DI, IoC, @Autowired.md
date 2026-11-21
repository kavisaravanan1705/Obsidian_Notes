# 📘 Spring Boot – Dependency Injection (DI), IoC, @Autowired

---

## 🔹 First Understand Project Flow (VERY IMPORTANT)

> [!tip] 3 Layer Architecture
> 
> - **Presentation Layer (Controller)** → Handles user request
> - **Service Layer** → Contains business logic (processing)
> - **Persistence Layer (Repository)** → Communicates with Database

### 🧠 Flow

```
User → Controller → Service → Repository → Response
```

> [!example] Example `User → /todo → Controller → Service → Repository → DB → return "hello todo"`

> [!abstract] Simple Meaning
> 
> - **Controller** → takes the request
> - **Service** → thinks / applies logic
> - **Repository** → gets data from DB

---

## 🔹 What is Inversion of Control (IoC)?

> [!note] Definition Giving the control of **object creation and management** to Spring instead of creating it manually is called **Inversion of Control (IoC)**.

### 🧠 Normal Java — Without IoC

```java
User user = new User();
```

> ❌ You create the object manually

### 🧠 With Spring — IoC

> ✅ Spring creates the object **automatically**

> [!abstract] Simple Meaning You don't control objects → **Spring controls objects**

---

## 🔹 What is Dependency Injection (DI)?

> [!note] Definition Dependency Injection means **giving required objects (dependencies) to a class** instead of creating them inside the class.

> [!abstract] Simple Meaning **"Don't create → just receive"**

### 🔍 Example — Controller needs Service

❌ **Wrong way:**

```java
Service s = new Service();
```

✅ **Correct way (DI):**

```java
@Autowired
Service s;
```

> Spring gives the `Service` object automatically.

---

## 🔹 What is `@Autowired`?

> [!note] Definition `@Autowired` is used to **automatically inject** a dependency (object) into a class.

> [!abstract] Simple Meaning **"Spring, please give me this object"**

> [!tip] Important Line "IoC is giving control to Spring to create and manage objects, and `@Autowired` is used to inject those objects where needed."

---

## 📦 Full Project Code — Explained

### 🔹 Model Class

```java
package dev.codeio.HelloWorld;

public class User {
    public String username;
    public String password;
}
```

> This class **holds data** (username and password).

---

### 🔹 Controller

```java
package dev.codeio.HelloWorld;

import org.springframework.web.bind.annotation.*;

@RestController
public class HelloWorldController {

    @PostMapping("/create")
    public String createUrl(@RequestBody User u) {
        return "Username : " + u.username + " Password:" + u.password;
    }
}
```

### 🔍 What happens here?

1. User sends JSON from Postman
2. Spring converts JSON → `User` object
3. Controller receives it
4. Returns response

---

### 🔹 application.properties

```properties
spring.application.name=HelloWorld
server.port=8081
```

> [!info] Meaning
> 
> - App name = `HelloWorld`
> - Runs on port `8081`

---

### 🔹 Main Class

```java
package dev.codeio.HelloWorld;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class HelloWorldApplication {

    public static void main(String[] args) {
        SpringApplication.run(HelloWorldApplication.class, args);
    }
}
```

> Starts your entire application.

---

### 🔹 Test Class

```java
package dev.codeio.HelloWorld;

import org.junit.jupiter.api.Test;
import org.springframework.boot.test.context.SpringBootTest;

@SpringBootTest
class HelloWorldApplicationTests {

    @Test
    void contextLoads() {
    }
}
```

> [!tip] Used for testing — you can ignore this for now.

---

## 🔥 Now Add DI — Important Upgrade

### 🔹 Service Layer

```java
package dev.codeio.HelloWorld;

import org.springframework.stereotype.Service;

@Service
public class UserService {

    public String process(User u) {
        return "Username : " + u.username + " Password:" + u.password;
    }
}
```

---

### 🔹 Controller with `@Autowired`

```java
package dev.codeio.HelloWorld;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

@RestController
public class HelloWorldController {

    @Autowired
    UserService service;

    @PostMapping("/create")
    public String createUrl(@RequestBody User u) {
        return service.process(u);
    }
}
```

> [!success] What Changed?
> 
> - ✅ Controller is **NOT creating** the Service
> - ✅ Spring is **injecting** it automatically via `@Autowired`

---

### 🔥 Flow Now

```
User → Controller → Service → Response
```

1. Controller gets the request
2. Service handles the logic
3. Response is returned

---

### 🧠 Real-Life Example

> [!example] Restaurant 🍽️
> 
> - **Customer** → Controller
> - **Chef** → Service
> - **Kitchen storage** → Repository
> 
> You don't cook yourself → Chef (Service) does it for you.

---

## 📘 What is `process(u)`? — Explained

Look at this line:

```java
return service.process(u);
```

### 🔹 Break It Word by Word

|Part|Meaning|
|---|---|
|`service`|Object of `UserService`, given by Spring via `@Autowired`|
|`process`|Method (function) defined inside `UserService`|
|`(u)`|`u` is the `User` object coming from `@RequestBody`|

---

### 🔹 Where is `process()` defined?

```java
@Service
public class UserService {

    public String process(User u) {
        return "Username : " + u.username + " Password:" + u.password;
    }
}
```

---

### 🔹 Full Flow — Step by Step

**Step 1:** You send from Postman:

```json
{
  "username": "admin",
  "password": "1234"
}
```

**Step 2:** Spring converts JSON → `User u`

**Step 3:** Controller receives it:

```java
public String createUrl(@RequestBody User u)
```

**Step 4:** This line runs:

```java
service.process(u);
```

→ Calls `process()` method and passes `u` (user data)

**Step 5:** Inside service:

```java
return "Username : " + u.username + " Password:" + u.password;
```

**Step 6:** Response goes back to the user ✅

---

> [!abstract] Simple Meaning `process(u)` = **"Send user data to service and process it"**

---

### 🧠 Real-Life Example

> [!example] Waiter & Chef 🍽️
> 
> - **Controller** = Waiter
> - **Service** = Chef
> 
> Waiter gives order → `process(u)` Chef prepares and returns the food 🍕

---

## 🔥 Placement-Level Answers

> [!success] ❓ What is IoC? "Inversion of Control means Spring manages object creation and lifecycle instead of the developer."

> [!success] ❓ What is Dependency Injection? "Dependency Injection is a technique where Spring provides required objects to a class instead of the class creating them."

> [!success] ❓ What is `@Autowired`? "@Autowired is used to automatically inject dependencies into a class."

> [!success] ❓ What is `process(u)`? "It is a method call where the controller passes the User object to the service layer for processing business logic."

---

## 🧠 Final Memory

> [!abstract] 3-Line Summary
> 
> - **IoC** → Spring controls object creation
> - **DI** → Spring gives objects where needed
> - **`@Autowired`** → how you ask Spring for an object

> [!abstract] One Line for `process(u)` `process(u)` = calling the service method with user data