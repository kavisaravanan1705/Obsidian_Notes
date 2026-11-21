# 📘 Spring Boot – URL Params, Path Variable, Request Param, Request Body

---

## 🔹 First Understand One Basic Idea

When **frontend** (browser / Postman) talks to **backend**:

> [!tip] Core Idea Frontend sends data to the API — this data can travel in **3 main ways:**
> 
> 1. Through the URL (Path Variable)
> 2. Through query parameters (Request Param)
> 3. Through request body — hidden data (Request Body)

---

## 🔹 1. Path Variable — `@PathVariable`

> [!note] What It Is Data is sent **inside the URL path** itself.

### 🧠 Real Example

```
http://localhost:8080/user/101
```

> Here `101` is a **dynamic value** — that is the Path Variable.

### 💻 Code Example

```java
@RestController
public class UserController {

    @GetMapping("/user/{id}")
    public String getUser(@PathVariable int id) {
        return "User ID is " + id;
    }
}
```

### 🔍 Flow

- URL → `/user/101`
- `id = 101`
- Output → `User ID is 101`

> [!abstract] Simple Meaning Value comes as **part of the URL path**

---

## 🔹 2. Request Param — `@RequestParam`

> [!note] What It Is Data is sent as **key=value** pairs in the URL.

### 🧠 Real Example

```
http://localhost:8080/login?user=admin&pass=1234
```

### 💻 Code Example

```java
@GetMapping("/login")
public String login(@RequestParam String user,
                    @RequestParam String pass) {
    return "User: " + user + " Password: " + pass;
}
```

### 🔍 Flow

- URL → `?user=admin&pass=1234`
- `user = admin`
- `pass = 1234`

> [!warning] Problem Username & password are **visible in the URL** ❌ — this is **not secure**.

> [!abstract] Simple Meaning Data comes **after `?` in the URL**

---

## 🔹 3. Request Body — `@RequestBody`

> [!note] What It Is Data is sent **inside the request body** — hidden and secure.

> [!tip] Your Important Point ✅ While using `@RequestBody`, we do **not** send username & password in the URL. We send it inside the body → much more secure.

### 💻 Example Program — Login API

**Step 1: Create Model Class**

```java
public class LoginRequest {
    public String userId;
    public String password;
}
```

**Step 2: Controller**

```java
@RestController
public class LoginController {

    @PostMapping("/login")
    public String login(@RequestBody LoginRequest request) {
        return "User: " + request.userId +
               " Password: " + request.password;
    }
}
```

---

### 🔹 How to Test in Postman

> [!example] Steps
> 
> 1. Open Postman
> 2. Select method → **POST**
> 3. Paste URL:
> 
> ```
> http://localhost:8080/login
> ```
> 
> 4. Go to: **Body → Raw → JSON**
> 5. Type:
> 
> ```json
> {
>     "userId": "admin",
>     "password": "1234"
> }
> ```
> 
> 6. Click **Send**

### 🔍 Flow

- Data is sent in the **body** (not in the URL)
- Spring automatically converts JSON → Java object
- Access values using `request.userId`, `request.password`

> [!abstract] Simple Meaning Data is **hidden inside the body** — the secure way

---

## 🔥 Important Difference Table (Interview Ready)

|Feature|Path Variable|Request Param|Request Body|
|---|---|---|---|
|Where data is|URL path|URL (`?key=value`)|Body|
|Security|❌ Low|❌ Low|✅ High|
|Use case|IDs|Small data|Sensitive data|

---

## 🔥 Real-Life Example — Instagram Login

> [!warning] Wrong Way ❌
> 
> ```
> /login?user=admin&pass=1234
> ```
> 
> Anyone can see the password in the URL!

> [!success] Correct Way ✅
> 
> ```json
> {
>   "userId": "admin",
>   "password": "1234"
> }
> ```
> 
> Sent inside the body → **secure** 🔒

---

## 🧠 Placement-Level Explanation

> [!success] If Interviewer Asks: "Why use `@RequestBody` instead of `@RequestParam`?" **Say this:**
> 
> "@RequestBody is used to send data securely in the HTTP request body, especially for sensitive information like login credentials, whereas @RequestParam sends data in the URL which is less secure and visible."

---

## 🧠 Final Memory Trick

> [!abstract] 3-Line Summary
> 
> - **Path** → data is inside the URL
> - **Param** → data comes after `?`
> - **Body** → data is hidden (secure)


## HTTP mapping annotations

Spring Boot provides specialized annotations for different HTTP methods.

|Annotation|Purpose|
|---|---|
|`@GetMapping`|Retrieve data|
|`@PostMapping`|Create/submit data|
|`@PutMapping`|Update/replace data|
|`@PatchMapping`|Partially update data|
|`@DeleteMapping`|Delete data|

### Remember this simple concept

```
@RequestMapping("/api")
```

Common URL for the controller.

```
@GetMapping("/students")
```

Retrieve students.

```
@PostMapping("/students")
```

Create a student.

```
@PutMapping("/students")
```

Update a student.

```
@DeleteMapping("/students")
```

Delete a student.

Your response:

```
{
  "category": "Programming",
  "description": "Basic Java questions",
  "difficulty": "Easy",
  "id": 4,
  "title": "Java Basics"
}
```

### What happened?

1. Postman sent your quiz data as JSON.
    
2. `@RequestBody` converted the JSON into a `Quiz` object.
    
3. `QuizController` called `service.createQuiz(quiz)`.
    
4. `QuizService` called `quizRepository.save(quiz)`.
    
5. PostgreSQL saved the quiz and generated ID `4`.
    
6. The saved quiz was returned as JSON.
    

Why is the ID 4? PostgreSQL generated it automatically because your entity uses:

```
@GeneratedValue(strategy = GenerationType.IDENTITY)
```