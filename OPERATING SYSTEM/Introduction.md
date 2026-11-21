# Operating System - Introduction Notes

> Interview-focused notes (Part 1)

------------------------------------------------------------------------

# 1. What is an Operating System (OS)?

## Definition

An **Operating System (OS)** is **system software** that acts as an
**interface (intermediary)** between the **user** and the **computer
hardware**. It manages hardware resources and provides an environment
for executing programs.

### Examples

-   Windows
-   Linux
-   macOS
-   Android

------------------------------------------------------------------------

# 2. OS as an Intermediary

## Intermediary

**Intermediary = Middleman**

Flow:

``` text
User
 ↓
Operating System
 ↓
Hardware
```

The user never communicates with hardware directly. The OS receives the
user's request and communicates with the hardware.

### Example

When you double-click Chrome:

``` text
You
 ↓
Operating System
 ↓
CPU / RAM / Disk
 ↓
Chrome Opens
```

------------------------------------------------------------------------

# 3. Why doesn't the user access hardware directly?

The OS prevents direct hardware access because it:

-   Protects hardware
-   Prevents conflicts between programs
-   Improves security
-   Manages resources efficiently

Instead of:

``` text
User → CPU
```

It becomes:

``` text
User
 ↓
OS
 ↓
CPU
```

------------------------------------------------------------------------

# 4. System Resources

Resources are components required by programs.

Examples: - CPU - Memory (RAM) - Hard Disk / SSD - Keyboard - Mouse -
Printer - Monitor - Internet

### Resource Management

If Chrome, VS Code and Spotify all need the CPU, the OS schedules CPU
time so every program gets a chance to run.

------------------------------------------------------------------------

# 5. Environment for Program Execution

The OS provides everything required to run programs.

Example: - CPU - RAM - Keyboard - Mouse - Storage - Display

The OS makes program execution:

-   Convenient (easy for users)
-   Efficient (good performance with proper resource usage)

------------------------------------------------------------------------

# 6. OS Runs All the Time

The OS is also a program.

Difference:

Normal Program:

``` text
Open
 ↓
Run
 ↓
Close
```

Operating System:

``` text
Computer ON
 ↓
OS Starts
 ↓
Keeps Running
 ↓
Computer OFF
```

The OS starts during booting and continues until shutdown.

------------------------------------------------------------------------

# 7. Resource Allocation

The OS assigns resources such as:

-   Memory (RAM)
-   Processor (CPU)
-   Input Devices
-   Output Devices

to **processes** that need them.

------------------------------------------------------------------------

# 8. Program vs Process

## Program

A file stored on disk.

Example: - Chrome.exe

## Process

A program that is currently running.

Flow:

``` text
Program
 ↓
Double Click
 ↓
Running
 ↓
Process
```

------------------------------------------------------------------------

# 9. Operating System and User Interaction

A general-purpose computer consists of:

-   Hardware
-   Operating System
-   System Programs
-   Application Programs

Structure:

``` text
User
 ↓
Application Programs
 ↓
System Programs
 ↓
Operating System
 ↓
Hardware
```

------------------------------------------------------------------------

# 10. Hardware

Hardware = Physical components that can be touched.

Examples:

-   CPU
-   ALU
-   RAM
-   Keyboard
-   Mouse
-   Monitor
-   Hard Disk

------------------------------------------------------------------------

# 11. CPU

**CPU = Central Processing Unit**

Known as the **Brain of the Computer**.

Functions: - Executes instructions - Performs calculations - Makes
decisions

------------------------------------------------------------------------

# 12. ALU

**ALU = Arithmetic Logic Unit**

Part of the CPU.

### Arithmetic Operations

-   Addition
-   Subtraction
-   Multiplication
-   Division

### Logical Operations

-   Greater than (\>)
-   Less than (\<)
-   Equal to (==)
-   Not equal (!=)

Returns **True** or **False**.

------------------------------------------------------------------------

# 13. Memory (RAM)

RAM temporarily stores programs and data currently being used.

Example: When Chrome opens, it is loaded into RAM.

RAM is **volatile memory**.

------------------------------------------------------------------------

# 14. Input and Output Devices

## Input Devices

Used to enter data.

Examples: - Keyboard - Mouse - Scanner - Webcam - Microphone

## Output Devices

Used to display results.

Examples: - Monitor - Printer - Speaker - Projector

------------------------------------------------------------------------

# 15. Peripheral Devices

External devices connected to the computer.

Examples: - Printer - Scanner - Webcam - USB Drive - External Hard Disk

------------------------------------------------------------------------

# 16. Storage Devices

Store data permanently.

Examples: - HDD - SSD - Pen Drive - CD/DVD

Storage is **non-volatile**.

------------------------------------------------------------------------

# 17. Memory vs Storage

  Memory (RAM)   Storage (HDD/SSD)
  -------------- -------------------
  Temporary      Permanent
  Volatile       Non-Volatile
  Faster         Slower than RAM

------------------------------------------------------------------------

# 18. System Programs

System programs help the Operating System manage the computer and
support other programs.

## Examples

### Compiler

Converts high-level language into machine language.

Flow:

``` text
Write Program
 ↓
Compiler
 ↓
Machine Code
```

### Loader

Loads the compiled program into RAM.

Flow:

``` text
Write Program
 ↓
Compile
 ↓
Loader
 ↓
RAM
 ↓
CPU Executes
```

### Editor

Software used to write code.

Examples: - VS Code - Eclipse - IntelliJ IDEA - Notepad++

### Operating System

The OS itself is also a system program because it manages the computer.

------------------------------------------------------------------------

# 19. Application Programs

Application programs are software used directly by users to perform
specific tasks.

Examples: - Chrome - Microsoft Word - WhatsApp - VLC - Photoshop -
Calculator

------------------------------------------------------------------------

# 20. System Program vs Application Program

  System Program                   Application Program
  -------------------------------- --------------------------
  Helps the Operating System       Helps the User
  Supports system operation        Performs user tasks
  Usually runs in the background   Opened directly by users
  Compiler, Loader, Editor         Chrome, Word, VLC

### Restaurant Analogy

**Kitchen Staff** → System Programs

**Food served to Customer** → Application Programs

------------------------------------------------------------------------

# 21. Application vs Application Program

There is **no technical difference**.

-   Application = Application Program

The second term is simply the full form used to distinguish it from
system programs.

------------------------------------------------------------------------

# 22. Volatile Memory

**Definition**

Volatile memory loses its contents when power is turned OFF.

Example: - RAM

Analogy: - Whiteboard (erase the writing and it disappears)

Flow:

``` text
Computer ON
 ↓
RAM Stores Data
 ↓
Power OFF
 ↓
RAM Becomes Empty
```

------------------------------------------------------------------------

# 23. Non-Volatile Storage

**Definition**

Non-volatile storage retains data even after power is turned OFF.

Examples: - HDD - SSD - Pen Drive - CD/DVD

Analogy: - Notebook (writing remains even after closing it)

------------------------------------------------------------------------

# 24. Volatile vs Non-Volatile

  Volatile Memory             Non-Volatile Storage
  --------------------------- ------------------------------
  RAM                         HDD, SSD, Pen Drive
  Temporary                   Permanent
  Data lost after power OFF   Data remains after power OFF
  Faster                      Slower than RAM

------------------------------------------------------------------------

# 25. Saving a File

``` text
Typing
 ↓
RAM

Click Save
 ↓
SSD / HDD

Power OFF

Saved file remains.
Unsaved work is lost.
```

------------------------------------------------------------------------

# Important Interview Questions

1.  What is an Operating System?
2.  Why can't users access hardware directly?
3.  What are system resources?
4.  Difference between Program and Process.
5.  What are the components of a computer system?
6.  What is the CPU?
7.  What is the ALU?
8.  Difference between RAM and Storage.
9.  What are system programs?
10. What are application programs?
11. Difference between system programs and application programs.
12. Is there any difference between an application and an application
    program?
13. What is volatile memory?
14. What is non-volatile storage?
15. Difference between volatile and non-volatile memory.