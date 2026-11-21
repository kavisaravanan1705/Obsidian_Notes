# 📌 H2 Database Connection – Mistake & Fix

---

## 🔴 Mistakes I Did

### 1. Missing Database Starter

| What I Did | What Was Missing |
|---|---|
| Added only `h2` dependency | Did not add Spring Boot database starter |

> **👉 Problem:** Spring Boot could not understand `spring.datasource.*` properties at all.

---

### 2. Wrong Spring Boot Version

```xml
<version>4.0.5</version>
```

> ⚠️ This version **does not exist** — caused dependency resolution to fail entirely.

---

### 3. Wrong Understanding

> 💭 I thought adding the H2 dependency alone was enough.
> But **H2 only provides the database engine** — it does NOT set up the connection.

```
H2 dependency  →  gives you the database
                  ❌ does NOT wire Spring Boot to it
```

---

## 🔍 How to Find Dependencies — Maven Repository

> 🌐 Website: **[https://mvnrepository.com](https://mvnrepository.com)**

---

### Step 1 — Search for H2 Database

1. Go to `https://mvnrepository.com`
2. In the search bar, type → `H2 Database`
3. Click on **H2 Database Engine** (by `com.h2database`)
4. Select the latest stable version
5. Copy the Maven dependency:

```xml
<dependency>
    <groupId>com.h2database</groupId>
    <artifactId>h2</artifactId>
    <scope>runtime</scope>
</dependency>
```

---

### Step 2 — Search for Spring Boot Starter Data JPA

1. In the search bar, type → `Spring Boot Starter Data JPA`
2. Click on **spring-boot-starter-data-jpa** (by `org.springframework.boot`)
3. Select the version that matches your Spring Boot version (e.g. `3.3.5`)
4. Copy the Maven dependency:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
```

---

### Step 3 — Paste into `pom.xml`

- Open your project's `pom.xml`
- Paste both dependencies inside the `<dependencies>` block
- Save the file, then **Reload Maven** (right-click `pom.xml` → Maven → Reload Project)

> ✅ Maven will automatically download the JARs and wire everything up.

---

## ✅ Fixes I Applied

### ✔ 1. Added the Correct Dependency

```xml
spring-boot-starter-data-jpa
```

**👉 This dependency tells Spring Boot to:**
- Connect to the database
- Auto-configure the datasource
- Load the H2 driver automatically

---

### ✔ 2. Fixed the Spring Boot Version

```xml
<version>3.3.5</version>
```

---

### ✔ 3. Reloaded Maven

- Dependencies downloaded properly
- All errors removed

---

## ✅ Why It Works Now

| Step | What Happens |
|---|---|
| 1 | Spring Boot reads `application.properties` |
| 2 | H2 driver is detected and loaded |
| 3 | Datasource connection is created automatically |
| 4 | H2 console becomes accessible |

---

## 🔥 Easy Mental Model

**Before Fix**
```
H2 alone  →  Database exists, but no connection ❌
```

**After Fix**
```
H2  +  spring-boot-starter-data-jpa  →  Connected DB ✅
```

---

## ⚠️ Important Note — In-Memory Database

```
jdbc:h2:mem:tododb
```

| Property | Detail |
|---|---|
| Type | In-memory database |
| Persistence | **Temporary** — data is lost when the app stops |
| Use case | Development & testing only |

---

## 🧾 Final Conclusion *(Exam Ready)*

> The issue occurred due to **two root causes**:
> 1. Missing `spring-boot-starter-data-jpa` dependency
> 2. Invalid Spring Boot version (`4.0.5` doesn't exist)
>
> After adding the correct dependency and fixing the version to `3.3.5`, Spring Boot successfully **auto-configured and connected** the H2 in-memory database.

---

## 📄 Correct `pom.xml`

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
         https://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.3.5</version>      <!-- ✅ Valid version -->
        <relativePath/>
    </parent>

    <groupId>dev.codeio</groupId>
    <artifactId>HelloSpringBoot</artifactId>
    <version>0.0.1-SNAPSHOT</version>

    <properties>
        <java.version>17</java.version>
    </properties>

    <dependencies>

        <!-- Web -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- ✅ Database Starter (CRITICAL — was missing before) -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

        <!-- H2 In-Memory Database -->
        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <scope>runtime</scope>
        </dependency>

    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>
```