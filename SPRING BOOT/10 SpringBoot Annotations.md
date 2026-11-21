# Spring Boot Core Annotations

> \(!abstract\) What this note covers These notes explain  
> **configuration**, `@Configuration`, `@Bean`, `@Component`,  
> `@Service`, `@Controller`, `@Repository`, `@ComponentScan`, and  
> `@EnableAutoConfiguration` in simple language, with examples and  
> placement questions.

## 1. First, what does "configuration" mean?

**Configuration means instructions or settings that tell an application  
how it should work.**

Think about setting up a new computer. You may need to set up the  
internet, sound, and display. Configuration is the setup information  
that helps the computer work as you want.

In Spring Boot, configuration can tell Spring things such as:

- which objects it should manage;
- which objects should be available for other classes to use;
- which framework features should be set up;
- which application settings or properties should be used.

Configuration does **not** mean writing all the business logic of the  
application. It is about setup and behavior.

### Everyday example

Imagine a library application:

- The **controller** receives a request to show a book.
- The **service** contains the logic for handling that request.
- The **repository** deals with retrieving book data.
- Spring configuration helps the application connect and manage these  
    parts.

## 2. What is a Spring Bean?

A **Spring Bean** is an object that is created, configured, and managed  
by the Spring container.

Why is this useful? If one class needs another object, Spring can  
provide the managed object through dependency injection rather than  
making the class responsible for creating every dependency itself.

For example, a `BookController` may need a `BookService`. If Spring  
manages both and their dependencies are configured correctly, Spring can  
inject the service into the controller.

> \(!important\) Remember A Java object is not automatically a Spring  
> Bean just because it is an ordinary class. It must be registered with  
> Spring, for example through component scanning or a `@Bean` method.

## 3. `@Configuration`

### What does it mean?

`@Configuration` marks a class as a source of Spring bean definitions  
and configuration.

In simple words, it tells Spring:

> "This class contains setup instructions for the application."

It is **not necessary on every Java class**. It is used on classes that  
provide configuration.

### Example

```
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {

    @Bean
    public String libraryName() {
        return "City Library";
    }
}
```

Understand the important parts:

- `@Configuration`: marks `AppConfig` as a configuration class.
- `@Bean`: tells Spring to register the object returned by this method  
    as a Spring Bean.
- `libraryName()`: returns the `String` object that Spring will manage  
    as a Bean.

This is a small demonstration. In real applications, `@Bean` methods are  
often used to configure objects from libraries or objects that need  
custom setup.

### Why not put `@Configuration` on every class?

Because most classes do not contain bean-definition setup instructions.  
Classes with application responsibilities usually use stereotype  
annotations such as `@Service`, `@Controller`, or `@Repository`.

## 4. `@Bean` versus `@Component`

These annotations are related to registering objects with Spring, but  
they work differently.

---

Annotation Where it is used What it tells Spring

---

`@Component` On a class Discover this class  
through component  
scanning and register  
it as a Bean.

`@Bean` On a method Register the object  
returned by this method  
as a Bean.

`@Configuration` On a class This class provides  
configuration, often  
including `@Bean`  
methods.

---

### When would you use `@Component`?

Use it when you own a class and want Spring to discover it through  
component scanning.

```
import org.springframework.stereotype.Component;

@Component
public class BookHelper {

    public void printMessage() {
        System.out.println("Welcome to the library");
    }
}
```

If the package containing `BookHelper` is scanned, Spring can register  
it as a Bean.

### When would you use `@Bean`?

Use it when you want to register an object through a method---for  
example, when configuring a third-party library class or creating an  
object with custom setup.

```
@Configuration
public class AppConfig {

    @Bean
    public BookHelper bookHelper() {
        return new BookHelper();
    }
}
```

This is an alternative registration style for the example. In a real  
application, do not register the same class both through component  
scanning and through a `@Bean` method unless you intentionally want  
separate Beans and understand the consequences.

## 5. `@Component` and its specialized annotations

### What is `@Component`?

`@Component` is a general-purpose annotation that marks a class as a  
Spring-managed component. If component scanning discovers the class,  
Spring can register it as a Bean.

### Can we use `@Component` for controller, service, and repository classes?

For simple component registration, a plain `@Component` can be enough.  
However, Spring provides specialized annotations because they  
communicate each class's role, and some have framework-specific  
behavior.

---

Annotation Typical responsibility Simple way to remember

---

`@Component` General Spring-managed General component  
class

`@Service` Business logic Service layer

`@Controller` Spring MVC web requests Web/controller layer  
and controller behavior

## `@Repository` Data-access layer Database-access layer

`@Service`, `@Repository`, and `@Controller` are specialized stereotype  
annotations built on `@Component`.

### Example: `@Component` versus `@Service`

With `@Component`:

```
@Component
public class BookService {
    public void displayBook() {
        System.out.println("Book details");
    }
}
```

With `@Service`:

```
@Service
public class BookService {
    public void displayBook() {
        System.out.println("Book details");
    }
}
```

Both can register the class as a Spring Bean when component scanning  
finds it. **Prefer `@Service` for business logic** because it  
communicates the class's purpose more clearly.

> \(!important\) A useful distinction `@Service` does not make Spring  
> find a class anywhere on the computer. The class must still be within  
> the packages Spring scans, or be registered another way.

`@Repository` can also participate in persistence exception translation  
when the relevant Spring persistence infrastructure is configured.  
`@Controller` has web-framework meaning, so plain `@Component` should  
not be treated as a complete replacement for every specialized  
annotation.

## 6. `@ComponentScan`

### What problem does it solve?

Annotations such as `@Component` and `@Service` mark classes for Spring.  
But Spring must still **find** those classes.

`@ComponentScan` tells Spring which packages to search for components.

### Everyday example

Imagine an event organizer needs to find students who registered for an  
event:

- A student's registration label is like `@Service` or `@Component`.
- The classrooms the organizer checks are like the packages Spring  
    scans.
- The search process is like component scanning.

If the organizer checks only certain classrooms, they might miss  
students in a classroom outside that area. Similarly, Spring may not  
find a class outside the scanned packages.

### Example project structure

```
com.example.library
├── LibraryApplication.java
├── service
│   └── BookService.java       (@Service)
├── controller
│   └── BookController.java    (@Controller)
└── repository
    └── BookRepository.java   (@Repository)
```

If the main application class is in `com.example.library`, the default  
component scan from `@SpringBootApplication` includes that package and  
its subpackages.

### Explicit `@ComponentScan` example

```
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;

@Configuration
@ComponentScan(basePackages = "com.example.payment")
public class AppConfig {
}
```

Here, Spring is instructed to scan `com.example.payment` and its  
subpackages for components.

### Do we need to write `@ComponentScan` on every project?

Usually, **no**. `@SpringBootApplication` already includes component  
scanning. Adding a plain `@ComponentScan` to the main application class  
is often redundant unless you need to customize the scan.

### What if a class is outside the scanned package?

Spring might not discover its Bean. If another class requires that Bean  
through dependency injection, application startup may fail with a  
missing-Bean or "no qualifying bean" error.

**Good practice:** Place the main application class in a common root  
package so the application packages are underneath it.

## 7. `@EnableAutoConfiguration`

### What does the name mean?

- **Enable** = turn on
- **Auto** = automatically
- **Configuration** = setup instructions and settings

`@EnableAutoConfiguration` enables Spring Boot's automatic configuration  
mechanism.

In simple words:

> "Spring Boot, examine my project and apply suitable framework  
> configuration when the required conditions are met."

### Everyday example

When setting up a new computer, you might prefer it to configure common  
features automatically instead of making you set up every detail by  
hand.

Spring Boot does something similar for application infrastructure. It  
uses information such as available dependencies, existing Beans,  
properties, and conditions to decide which configurations are suitable.

### How does it work?

Suppose you add the Spring Web dependency to your project. Spring Boot  
can consider web-related auto-configurations. It checks conditions and  
applies suitable configuration when those conditions match.

A simplified view:

```
Your project dependencies and settings
                 |
                 v
     Spring Boot checks conditions
                 |
                 v
 Suitable auto-configurations are applied
                 |
                 v
 Common framework setup is handled for you
```

This is a simplified overview, not a claim that every configuration  
follows exactly the same checks.

### What does auto-configuration NOT do?

It does **not**:

- write all your business logic;
- automatically create every class your application needs;
- configure every feature regardless of conditions;
- replace component scanning.

For example, it will not write the business logic inside your  
`PaymentService`.

### Conditional configuration

"Conditional" means **something happens only if a requirement is  
satisfied**.

Spring Boot auto-configurations use conditions such as these:

---

Annotation Meaning

---

`@ConditionalOnClass` A configuration can apply if a  
required class is available.

`@ConditionalOnMissingBean` A configuration can apply if a  
matching Bean is not already  
present.

`@ConditionalOnProperty` A configuration can apply when a  
property matches the specified  
condition.

---

These annotations are used in auto-configuration and other conditional  
configuration scenarios. The exact conditions depend on the  
configuration.

### What does "backing off" mean?

Suppose Spring Boot has a default configuration that creates a  
particular Bean only when a matching Bean is missing. You define your  
own matching Bean.

If that default configuration uses `@ConditionalOnMissingBean`, Spring  
Boot can skip creating its default Bean because yours already exists.

This is called **backing off**.

> \(!warning\) Important nuance Backing off is not a universal rule for  
> every Spring Bean. It depends on the conditions in the relevant  
> auto-configuration.

## 8. How `@SpringBootApplication` connects these concepts

A typical Spring Boot main class looks like this:

```
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class LibraryApplication {

    public static void main(String[] args) {
        SpringApplication.run(LibraryApplication.class, args);
    }
}
```

`@SpringBootApplication` combines three major annotations:

---

Included annotation Main responsibility

---

`@SpringBootConfiguration` (a Marks the application class as a  
specialized `@Configuration`) source of configuration.

`@EnableAutoConfiguration` Enables conditional automatic  
framework configuration.

`@ComponentScan` Finds component classes in the scan  
scope.

---

So, in an ordinary Spring Boot application, you usually do not need to  
add all three annotations separately.

### Remember the difference

- **`@Configuration`**: "This class provides configuration  
    instructions."
- **`@ComponentScan`**: "Search these packages for component classes."
- **`@EnableAutoConfiguration`**: "Apply suitable framework  
    configuration automatically when conditions match."
- **`@Component`**: "This class can be discovered and registered as a  
    Spring Bean."

## 9. Placement interview questions

### Q1. What is `@Configuration`?

It marks a class as a source of Spring configuration and bean  
definitions.

### Q2. What is the difference between `@Bean` and `@Component`?

`@Component` marks a class for component scanning. `@Bean` marks a  
method whose returned object should be registered as a Spring Bean.

### Q3. Can `@Component` replace `@Service`?

For basic component registration, often yes. However, `@Service` is  
preferred for business-logic classes because it communicates their role.

### Q4. What does `@ComponentScan` do?

It tells Spring which packages to scan to discover components and  
register them as Beans.

### Q5. Is `@ComponentScan` required with `@SpringBootApplication`?

Usually, no. `@SpringBootApplication` already includes component  
scanning.

### Q6. What does `@EnableAutoConfiguration` do?

It enables Spring Boot's mechanism for applying suitable framework  
configuration based on dependencies, existing Beans, properties, and  
conditions.

### Q7. What is conditional auto-configuration?

It means a configuration is applied only when its specified conditions  
are satisfied.

### Q8. What does "backing off" mean?

A conditional default configuration may skip creating a default Bean  
when an appropriate user-defined Bean already exists.

### Q9. Does auto-configuration write business logic?

No. It helps configure framework infrastructure; developers still write  
their application's business logic.

## 10. Self-test

Try answering these without looking at the explanations.

1. Which annotation marks a general-purpose Spring component?
2. Which annotation is normally preferred for business-logic classes?
3. Which annotation tells Spring where to search for components?
4. Which annotation enables Spring Boot's automatic configuration  
    mechanism?
5. Which annotation is used on a method to register its returned object  
    as a Bean?
6. Does `@Service` guarantee that Spring will find the class regardless  
    of its package?
7. If a conditional default configuration uses  
    `@ConditionalOnMissingBean` and a matching Bean already exists, what  
    may happen?
8. Which three major annotations are combined by  
    `@SpringBootApplication`?

### Answers

1. `@Component`
2. `@Service`
3. `@ComponentScan`
4. `@EnableAutoConfiguration`
5. `@Bean`
6. No. The class must be discovered by component scanning or registered  
    another way.
7. Spring Boot may back off and skip that default Bean configuration.
8. `@SpringBootConfiguration`, `@EnableAutoConfiguration`, and  
    `@ComponentScan`.

## 11. One-minute revision

---

If you hear... Think...

---

"Configuration instructions" `@Configuration`

"Register the object returned by `@Bean`  
this method"

"General Spring-managed class" `@Component`

"Business logic" `@Service`

"Find annotated classes in `@ComponentScan`  
packages"

"Set up framework features `@EnableAutoConfiguration`  
automatically when conditions  
match"

## "The default configuration skips Backing off  
its Bean because mine exists"

> \(!tip\) Study order First understand what a Spring Bean is. Then  
> learn `@Component` and its specialized annotations, followed by  
> `@Configuration` and `@Bean`. After that, study `@ComponentScan`, then  
> `@EnableAutoConfiguration`, and finally how they combine inside  
> `@SpringBootApplication`.