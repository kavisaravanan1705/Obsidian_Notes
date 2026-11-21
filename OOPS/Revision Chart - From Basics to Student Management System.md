---

tags:

- java
- oop
- notes aliases:
- Java OOP Notes
- Student Management System cssclasses:
- java-notes

---

# 1. Classes and Objects

## Class = blueprint

A class defines what an object contains.

```java
class Student {
    String name;
    int registerNumber;
    String department;
    int year;
}
```

## Object = actual instance of that class

```java
Student s1 = new Student();
Student s2 = new Student();
```

- `Student` is the class/type.
- `s1` and `s2` are reference variables.
- `new Student()` creates an object.
- Each object has its own fields.

### Two different objects

> [!example] s1 Name: Kavi
> 
> Reg: 101

> [!example] s2 Name: Ravi
> 
> Reg: 102

Each object has its own independent field values.

---

# 2. Constructors

A constructor initializes an object when you create it.

```java
class Student {
    String name;
    int registerNumber;
    String department;
    int year;

    Student(String name, int registerNumber, String department, int year) {
        this.name = name;
        this.registerNumber = registerNumber;
        this.department = department;
        this.year = year;
    }
}
```

Creating an object:

```java
Student s1 = new Student("Kavi", 101, "CSE", 2);
```

> [!note] Remember
> 
> |Concept|Meaning|
> |---|---|
> |Constructor|Initializes object|
> |Constructor name|Must match class name|
> |Constructor return type|No return type, not even `void`|
> |`this.name`|Field belonging to the current object|
> |`name`|Parameter passed to constructor|

## Why `this`?

```java
this.name = name;
```

- Left side → object field.
- Right side → parameter.

---

# 3. Object References

> [!info] This was an important topic we practised.

```java
Student s1 = new Student("Kavi", 101, "CSE", 2);
Student s2 = s1;
```

Both references point to the same object.

## Reference assignment

```java
s2 = s1;
```

No new object is created. Both variables refer to the same object.

## Reassigning

```java
s1 = new Student("Ravi", 102, "ECE", 3);
```

Now `s1` points to a new object, but `s2` still points to the old object.

## Changing an object

```java
s2.setName("Priya");
```

Changes the name in the object that `s2` points to.

> [!important] Key rule Copying a reference is not copying an object.

---

# 4. Encapsulation — private fields, getters and setters

## Private fields

```java
class Student {
    private String name;
    private int registerNumber;
    private String department;
    private int year;
}
```

`private` means the fields are directly accessible only within the same class.

## Getters — retrieve values

```java
public String getName() {
    return name;
}

public int getReg() {
    return registerNumber;
}

public String getDept() {
    return department;
}

public int getYear() {
    return year;
}
```

## Setters — modify values

```java
public void setName(String name) {
    this.name = name;
}

public void setReg(int reg) {
    this.registerNumber = reg;
}

public void setDept(String dept) {
    this.department = dept;
}

public void setYear(int year) {
    this.year = year;
}
```

|Getter|Setter|
|---|---|
|Returns a value|Changes a value|
|`getName()`|`setName("Ravi")`|
|Returns something|Usually returns `void`|

## Example

```java
Student s1 = new Student("Kavi", 101, "CSE", 2);

s1.setName("Priya");

System.out.println(s1.getName());
```

**Output:** `Priya`

## Validation example

```java
public void setName(String name) {
    if (name != null && name.length() > 3) {
        this.name = name;
    }
}
```

- `&&` means AND.
- Both conditions must be true.
- `name != null` is checked first.
- Short-circuiting prevents `name.length()` from executing when `name` is `null`.

---

# 5. ArrayList

An `ArrayList` stores multiple objects and can grow or shrink.

## Creating one

```java
import java.util.ArrayList;

ArrayList<Student> students = new ArrayList<>();
```

## Adding objects

```java
students.add(new Student("Kavi", 101, "CSE", 2));
students.add(new Student("Ravi", 102, "ECE", 3));
```

## Important methods

|Method|Purpose|
|---|---|
|`add()`|Add object|
|`get(index)`|Retrieve object at index|
|`size()`|Number of elements|
|`remove(index)`|Remove element at index|

## Retrieving an object

```java
Student s = students.get(0);
System.out.println(s.getName());
```

`students.get(0)` returns a `Student` reference, so you can call getters on it.

## Traditional for loop

```java
for (int i = 0; i < students.size(); i++) {
    Student s = students.get(i);
    System.out.println(s.getName());
}
```

## Enhanced for loop

```java
for (Student s : students) {
    System.out.println(s.getName());
}
```

### How the enhanced loop works

If 3 `Student` objects are stored, the loop executes 3 times.

1. `s` refers to the first `Student`.
2. `s` refers to the second `Student`.
3. `s` refers to the third `Student`.

## Removing

```java
students.remove(1);
```

Removes the element at index 1.

> [!warning] When removing while looping through an `ArrayList`, be careful: modifying it directly during an enhanced for loop can cause `ConcurrentModificationException`.

---

# 6. CRUD operations

> [!abstract] CRUD = Create, Read, Update, Delete These are the four fundamental operations used in many applications.

## C — Create

Add a new `Student`.

```java
students.add(new Student("Kavi", 101, "CSE", 2));
```

## R — Read

Display all students.

```java
for (Student s : students) {
    System.out.println(s.getName());
}
```

Search:

```java
int searchReg = 102;
boolean found = false;

for (Student s : students) {
    if (s.getReg() == searchReg) {
        found = true;
        System.out.println(s.getName());
        break;
    }
}

if (!found) {
    System.out.println("Student not found");
}
```

## U — Update

Find the object and modify it using setters.

```java
int searchReg = 102;
boolean found = false;

for (Student s : students) {
    if (s.getReg() == searchReg) {
        found = true;
        s.setDept("CSE");
        s.setYear(s.getYear() + 1);
        System.out.println("Updated");
        break;
    }
}

if (!found) {
    System.out.println("Student not found");
}
```

## D — Delete

```java
for (int i = 0; i < students.size(); i++) {
    if (students.get(i).getReg() == 102) {
        Student deletedStudent = students.get(i);
        students.remove(i);
        System.out.println(deletedStudent.getName() + " deleted");
        break;
    }
}
```

> [!question] Why save `deletedStudent` first? After removing the reference from the `ArrayList`, we can still use the local reference we saved to display the deleted student's details.

---

# 7. HashMap

A `HashMap` stores key-value pairs.

```java
import java.util.HashMap;

HashMap<Integer, Student> hash = new HashMap<>();
```

## Structure

|Key|Value|
|---|---|
|101|Kavi Student object|
|102|Ravi Student object|
|103|Priya Student object|

## Why `Integer` and `Student`?

```java
HashMap<Integer, Student>
```

- `Integer` → key type.
- `Student` → value type.
- Java generics use reference types, not primitive types such as `int`; `Integer` is the wrapper class for `int`.

## Add

```java
hash.put(101, new Student("Kavi", 101, "CSE", 2));
hash.put(102, new Student("Ravi", 102, "ECE", 3));
hash.put(103, new Student("Priya", 103, "IT", 2));
```

## Key HashMap methods

|Method|Purpose|
|---|---|
|`put(key, value)`|Insert or replace|
|`get(key)`|Retrieve value|
|`containsKey(key)`|Check if key exists|
|`remove(key)`|Delete entry|
|`size()`|Number of entries|
|`keySet()`|Get keys|
|`values()`|Get values|

## `put()` behaviour

```java
hash.put(101, new Student("Kavi", 101, "CSE", 2));
hash.put(101, new Student("Arun", 101, "ECE", 3));
```

> [!important] Same key = replacement The second entry replaces the value for key `101`. It does not create another entry with the same key.

## Retrieve

```java
Student s = hash.get(101);

System.out.println(s.getName());
```

`hash.get(101)` returns the `Student` object reference mapped to key `101`.

## Check

```java
if (hash.containsKey(101)) {
    System.out.println("Student exists");
}
```

## Update

```java
Student s = hash.get(101);

if (s != null) {
    s.setDept("ECE");
    s.setYear(s.getYear() + 1);
}
```

Because `s` references the `Student` object stored in the `HashMap`, changes made through `s` are visible through the `HashMap`.

## Delete

```java
if (hash.containsKey(101)) {
    Student s = hash.get(101);
    System.out.println(s.getName());
    hash.remove(101);
}
```

## Iterate through keys

```java
for (Integer key : hash.keySet()) {
    Student s = hash.get(key);
    System.out.println(s.getName());
}
```

## Iterate through values

```java
for (Student s : hash.values()) {
    System.out.println(s.getName());
}
```

> [!tip] Remember this difference `hash.keySet()`
> 
> You get keys, then use `hash.get(key)` to retrieve the corresponding object.
> 
> `hash.values()`
> 
> You get `Student` objects directly, so you don't need `hash.get()` inside the loop.

---

# 8. Scanner

You already know `Scanner`, so this is just a reminder.

```java
Scanner sc = new Scanner(System.in);
```

|Method|Input|
|---|---|
|`nextInt()`|Integer|
|`next()`|One word|
|`nextLine()`|Entire line including spaces|

Examples:

```java
int reg = sc.nextInt();
String name = sc.next();
String dept = sc.nextLine();
```

---

# 9. Menu-driven program — our current project

This is where we started combining everything.

## Menu structure

```text
----- Student Management System -----
1. Add Student
2. View All Students
3. Search Student
4. Update Student
5. Delete Student
6. Exit
```

## The basic structure

```java
int choice = 0;

while (choice != 6) {
    // Display menu
    // Read choice

    switch (choice) {
        case 1:
            // Add
            break;

        case 2:
            // View
            break;

        case 3:
            // Search
            break;

        case 4:
            // Update
            break;

        case 5:
            // Delete
            break;

        case 6:
            // Exit
            break;

        default:
            // Invalid choice
    }
}
```

## How the `while` and `switch` work together

### Execution flow

```text
while (choice != 6)
Check whether loop should continue

Display menu + read choice

switch(choice)
Execute the selected case

break exits switch
Then execution reaches the end of the while loop body

Check while condition again
```

## The important `break` distinction

```java
break;
```

Inside a `switch` exits the `switch`, not the surrounding `while` loop.

So for choice 1:

1. Menu appears.
2. User enters 1.
3. Case 1 executes.
4. Switch exits.
5. While condition is checked again.
6. Menu appears again.

For choice 6:

1. Menu appears.
2. User enters 6.
3. Case 6 executes.
4. Switch exits.
5. While checks `choice != 6`.
6. It is false.
7. Loop terminates.

That's why the exit option doesn't display the menu again.

---

# 10. What we've completed in our actual project

## Student Management System progress

1. **Menu + while + switch** — Completed You tested options, exit, and invalid choices.
2. **Case 1 — Add Student** — Started Reads name, register number, department and year; creates a `Student` object. We still need to store it in the `HashMap`.
3. **Case 2 — View All Students** — Code written Uses `hash.values()` and getters. We corrected a repeated `getYear()` mistake. You need to test it with students added during the same run.
4. **Case 3 — Search Student** — In progress We identified the simpler `HashMap` search approach and are about to implement it.
5. **Case 4 — Update** — Not implemented
6. **Case 5 — Delete** — Not implemented
7. **Case 6 — Exit** — Completed

## Case 1 — Add Student (current code idea)

You wrote this input logic:

```java
String name = sc.next();
int regNo = sc.nextInt();
String dept = sc.next();
int year = sc.nextInt();

Student s = new Student(name, regNo, dept, year);
```

The missing important step is storing that object in the `HashMap` using `put()`.

```java
hash.put(regNo, s);
```

Or combine both:

```java
hash.put(regNo, new Student(name, regNo, dept, year));
```

## Case 2 — View all students

The logic you wrote:

```java
for (Student s1 : hash.values()) {
    System.out.println(s1.getName());
    System.out.println(s1.getReg());
    System.out.println(s1.getDept());
    System.out.println(s1.getYear());
}
```

This is correct for displaying all `Student` objects stored in the `HashMap`.

## Case 3 — Search a student

> [!todo] This is our exact next step.

You do not need a loop when you already have the register number as the `HashMap` key.

The logic we discussed:

```java
if (hash.containsKey(number)) {
    Student s = hash.get(number);

    // Display details using getters
} else {
    // Student not found
}
```

We will finish this together, not skip ahead.

---

# 11. Why your data disappears after restarting

```java
HashMap<Integer, Student> hash = new HashMap<>();
```

This `HashMap` exists in the program's memory while the program runs.

|Storage|After program termination|
|---|---|
|HashMap|Lost|
|ArrayList|Lost|
|Text file|Remains|
|Database|Remains|

Later we will learn file handling to preserve student records between program runs.

---

# 12. Our learning roadmap from here

1. Classes, objects, constructors Completed
2. Object references Completed
3. Encapsulation — getters/setters Completed
4. ArrayList Completed
5. CRUD with ArrayList Completed
6. HashMap + CRUD Completed
7. Menu-driven Student Management System In progress — Search, Update, Delete, integration and debugging
8. Validation and integration practice
9. Library Management mini-project
10. Taxi Booking mini-project

---

# Quick reference — the syntax you will use most

|Task|Syntax|
|---|---|
|Create Student|`new Student(...)`|
|Add to HashMap|`hash.put(key, student)`|
|Retrieve|`hash.get(key)`|
|Check key|`hash.containsKey(key)`|
|Delete|`hash.remove(key)`|
|Get all values|`hash.values()`|
|Loop through values|`for (Student s : hash.values())`|
|Get name|`s.getName()`|
|Get reg|`s.getReg()`|
|Get dept|`s.getDept()`|
|Get year|`s.getYear()`|
|Change name|`s.setName("Ravi")`|
|Change dept|`s.setDept("CSE")`|
|Change year|`s.setYear(3)`|
|Loop menu|`while (choice != 6)`|
|Select operation|`switch(choice)`|
|Exit case|`case 6:`|