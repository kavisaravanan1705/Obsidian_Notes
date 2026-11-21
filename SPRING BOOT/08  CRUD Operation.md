# 🌟 Spring Boot CRUD – Complete Notes (Kavi)

---

# 🌱 1. What is CRUD?

CRUD = 4 basic operations:

- **Create** → Add data
- **Read** → View data
- **Update** → Modify data
- **Delete** → Remove data

---

# 🌱 2. Spring Boot Flow

```
Controller → Service → Repository → Database
```

---

# 🌱 3. Entity (Model)

```java
@Entity
@Data
public class Student {

    @Id
    @GeneratedValue
    long id;

    String title;
    String description;
    boolean isCompleted;
}
```

### 🧠 Notes

- `@Entity` → table
- `@Id` → primary key (mandatory)
- `@GeneratedValue` → auto ID
- `@Data` → auto getters/setters

---

# 🌱 4. Repository

```java
public interface HelloSpringBootRepository extends JpaRepository<Student, Long> {
}
```

### 🧠 Important

- `Student` → table
- `Long` → ID type
- No need to write methods

### Auto methods:

```
save()
findAll()
findById()
deleteById()
```

---

# 🌱 5. Service Layer

```java
@Service
public class HelloSpringBootService {

    @Autowired
    HelloSpringBootRepository repo;

    // CREATE
    public Student saveStudent(Student s) {
        return repo.save(s);
    }

    // READ ALL
    public List<Student> getAllStudents() {
        return repo.findAll();
    }

    // READ BY ID
    public Student getStudentById(Long id) {
        return repo.findById(id).orElse(null);
    }

    // UPDATE
    public Student updateStudent(Student s) {
        return repo.save(s);
    }

    // DELETE
    public void deleteStudent(Long id) {
        repo.deleteById(id);
    }
}
```

---

# 🌱 6. Controller

```java
@RestController
public class HelloSpringBootController {

    @Autowired
    HelloSpringBootService service;

    // CREATE
    @PostMapping("/add")
    public Student create(@RequestBody Student s) {
        return service.saveStudent(s);
    }

    // READ ALL
    @GetMapping("/all")
    public List<Student> getAll() {
        return service.getAllStudents();
    }

    // READ BY ID
    @GetMapping("/student/{id}")
    public Student getById(@PathVariable Long id) {
        return service.getStudentById(id);
    }

    // UPDATE
    @PutMapping("/update")
    public Student update(@RequestBody Student s) {
        return service.updateStudent(s);
    }

    // DELETE
    @DeleteMapping("/delete/{id}")
    public String delete(@PathVariable Long id) {
        service.deleteStudent(id);
        return "Deleted Successfully";
    }
}
```

---

# 🌱 7. HTTP Methods (VERY IMPORTANT)

|Method|Purpose|Body|Example|
|---|---|---|---|
|GET|Read|❌|`/all`|
|POST|Create|✅|`/add`|
|PUT|Update|✅|`/update`|
|DELETE|Delete|❌|`/delete/1`|

---

# 🌱 8. Postman Usage

### 🔹 CREATE (POST)

```
POST /add
```

```json
{
  "title": "Task",
  "description": "Learn",
  "isCompleted": false
}
```

---

### 🔹 READ ALL (GET)

```
GET /all
```

---

### 🔹 READ BY ID (GET)

```
GET /student/1
```

---

### 🔹 UPDATE (PUT)

```
PUT /update
```

```json
{
  "id": 1,
  "title": "Updated",
  "description": "Updated",
  "isCompleted": true
}
```

---

### 🔹 DELETE (DELETE)

```
DELETE /delete/1
```

---

# 🌱 9. Important Concepts

---

## 🔹 Why no method in repository?

Because:

```
extends JpaRepository → gives CRUD automatically
```

---

## 🔹 Why interface not class?

- Interface → define
- Spring → implement

---

## 🔹 What is `save()`?

```
save() = create OR update
```

- New ID → insert
- Existing ID → update

---

## 🔹 Why primary key mandatory?

- Identifies each row
- Required by JPA

---

## 🔹 Why `Student, Long`?

```
JpaRepository<Entity, ID_Type>
```

---

## 🔹 What is `@RequestBody Student s`?

- `Student` → type
- `s` → variable
- Converts JSON → object

---

## 🔹 Why GET has no input?

```
getAllStudents()
```

👉 No filter → no parameter

---

## 🔹 Why CREATE needs input?

```
createStudent(Student s)
```

👉 Need data to save

---

## 🔹 Why Optional?

```
findById() → may return data OR empty
```

---

## 🔹 Why return types differ?

|Operation|Return|
|---|---|
|CREATE|Student|
|READ|List<Student>|
|READ by ID|Student|
|UPDATE|Student|
|DELETE|String / void|

👉 Return type = what you send back

---

# 🌱 10. Common Errors

---

## ❌ 400 Bad Request

- Wrong JSON
- Wrong field names
- Lombok issue

---

## ❌ 405 Method Not Allowed

- Used GET instead of POST
- Wrong HTTP method

---

## ❌ 200 but no data

- ID not found
- DB empty

---

## ❌ Lombok Error

```
ExceptionInInitializerError
```

✔ Fix:

- Add dependency
- Enable annotation processing
- Install plugin

---

# 🌱 11. Execution Steps

```
1. Run app
2. POST (/add)
3. GET (/all)
4. GET (/student/{id})
5. PUT (/update)
6. DELETE (/delete/{id})
```

---

# 🌱 12. Final Flow

```
Controller → Service → Repository → Database
```

---

# 🧠 Final One-Line Summary

```
CRUD in Spring Boot uses JpaRepository methods:
save(), findAll(), findById(), deleteById()
```

---

# 🌱 13. Return Type Concept (IMPORTANT – As Asked)

Ahh 👍 this is a very smart question — you're noticing patterns now.

You're asking:

👉 Why sometimes we write

```java
public Student methodName(...)
```

👉 But in DELETE we wrote

```java
public String delete(...)
```

👉 And sometimes we don't use Student?

🌱 Key idea: Return type depends on what you want to send back

🧠 1. CREATE / READ / UPDATE

```java
public Student createStudent(...)
```

👉 Why Student?

👉 Because: 🗣️ "We are returning a Student object"

Example response:

```json
{
  "id": 1,
  "title": "Task",
  "description": "Learn",
  "isCompleted": false
}
```

🧠 2. READ ALL

```java
public List<Student> getAll()
```

👉 Why List<Student>?

👉 Because: 🗣️ "We return multiple students"

🧠 3. DELETE

```java
public String delete(...)
```

👉 Why String?

👉 Because: 🗣️ "We are returning a message"

Example:

```
Deleted Successfully
```

🌱 Important point

👉 Return type = what you want to send to user

🌱 Can we use Student in DELETE?

👉 Yes, but not needed

Example:

```java
public Student delete(Long id)
```

👉 But:

We don't have student after deleting ❌ So better to send message ✔️

🌱 Another option (better practice)

```java
public void delete(Long id)
```

👉 Means: 🗣️ "No return"

🌱 Simple analogy

👉 Think:

```
CREATE → return created object
READ   → return data
DELETE → just say "done"
```

🌱 Summary table

|Operation|Return type|Why|
|---|---|---|
|CREATE|Student|return saved data|
|READ|List<Student>|return all data|
|READ by ID|Student|return one data|
|UPDATE|Student|return updated data|
|DELETE|String / void|just confirmation|

🧠 One-line memory

👉 Return type = what you want to send back to user

---

# 🎉 You completed CRUD fully

---

# 🚀 Next Level (Optional)

- ResponseEntity
- Validation
- Exception Handling
- Frontend integration

---