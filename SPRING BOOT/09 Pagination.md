# 🌱 What is Pagination?

> [!info] Core Concept 👉 Instead of loading all data, we load small parts (pages)

**Example:**

```
Page 0 → first 5 records  
Page 1 → next 5 records  
Page 2 → next 5 records
```

---

## 🧠 Why Pagination?

|Benefit|Details|
|---|---|
|🚀 Faster|Only fetches what's needed|
|💾 Less Memory|Reduces load on server & client|
|🌍 Real Apps|Used by Amazon, Instagram & more|

---

## 🌱 Step 1: Repository _(no change)_

```java
public interface HelloSpringBootRepository extends JpaRepository<Student, Long> {
}
```

> [!success] Already supports pagination 😎

---

## 🌱 Step 2: Service

```java
import org.springframework.data.domain.Page;
import org.springframework.data.domain.PageRequest;

public Page<Student> getStudentsPaginated(int page, int size) {
    return repo.findAll(PageRequest.of(page, size));
}
```

### 🧠 Explanation

> [!note] `Page<Student>` 👉 Contains:
> 
> - ✅ data
> - ✅ total pages
> - ✅ current page

> [!note] `PageRequest.of(page, size)` 👉 Creates pagination request
> 
> **Example:**
> 
> ```
> page = 0, size = 5 → first 5 records
> ```

---

## 🌱 Step 3: Controller

```java
@GetMapping("/students")
public Page<Student> getPaginated(
        @RequestParam int page,
        @RequestParam int size) {
    return service.getStudentsPaginated(page, size);
}
```

### 🧠 Explanation

> [!note] `@RequestParam` 👉 Takes values from URL

---

## 🌱 How to Execute

> [!tip] Use browser or Postman:
> 
> ```
> http://localhost:8080/students?page=0&size=3
> ```

---

## 🌱 Output Example

```json
{
  "content": [
    { "id": 1, "title": "Task1" },
    { "id": 2, "title": "Task2" },
    { "id": 3, "title": "Task3" }
  ],
  "totalPages": 5,
  "totalElements": 15,
  "size": 3,
  "number": 0
}
```

---

## 🌱 Key Line

```java
repo.findAll(PageRequest.of(page, size));
```

> [!important] 👉 This = **PAGINATED READ**

---

## 🌱 Simple Understanding

```
page → which page  
size → how many records
```

---

## 🧠 One-Line Memory

> [!abstract] 💡 Quick Recall **Pagination** = `findAll(PageRequest.of(page, size))`

---

# 🌱 What is `findAll()`?

repo.findAll();

👉 It is a **method from JpaRepository**

👉 Meaning:  
🗣️ **“Get all records from database”**