Chapter Summaries of Java in a Nutshell 8e
===
# PDF Reference
https://dn721809.ca.archive.org/0/items/Vismay/1548-Java_in_a_Nutshell_8th.pdf

Opening this online enables you to jump to different parts of the textbook

In the PDF
- Part I Table of Contents is at Page
- Part II Table of Contents is at Page 350

# How to Consume a Textbook
1. Preview the chapter (5 min)
2. Actively read a section (15–25 min)
   - Summarize it aloud
   - Ask yourself questions
3. Take short notes (your own words)
4. After the section: close the book, recall the main ideas
5. Next day: quiz yourself or teach it to someone
6. Apply it in code
7. Repeat over spaced days

# Chapter 1
> This chapter is an overview of the Java language and the Java platform. It
explains the important features and benefits of Java, including the lifecycle
of a Java program. We also touch on Java security and answer some
criticisms of Java

Key Things to Define:
- Java
    - Language:
    - Execution Environment
    - Ecosystem
- Why Java?
- Java vs Python

## The Three Pillars of Java: Language, Execution Environment, and Ecosystem
### Language
Java is a verbose programming language designed to be human-readable and understandable. It came out in the 1990s as another option ontop of C and C++; and as such a lot of similarities can be drawn. **More syntactic details can be found in a later chapter**. While newer languages like JavaScript and Python have risen in popularity; *Java continues to remain widely used* in many production and enterprise-grade systems.

### Execution Environment
A **Java Virtual Machine (JVM)** is a runtime environment that executes *Java bytecode*. Java programs need the Java Virtual Machine (JVM) to be loaded in the compute unit to be able to execute.

A **runtime environment** is a specialized software layer thats designed to execute other programs on your machine. It manages the execution, resources (standard libraries, memory management, etc.) and errors

**Java Bytecode** is an intermediate, non-human-readable format produced by the Java compiler (javac). It's not specific to any one machine, making it portable across platforms that support the JVM.

The JVM is designed to make executing Java programs standardized and accessibile:
- Java programs to be run on *any hardware* that supports the JVM (can be developed on one machine and ran on a completely different one)
- *High backwards compatability* (e.g., the oldest Java program can be run on the most modern JVM and vice versa)

The JVM in particular:
- Reads and executes a *bytecode interpretation of the code*
- Leverages runtime analytics and information to find *the most commonly used functions in a program* and convert it to *native code to the specific machine's processor* to enable much faster processing. This is called **Just-In-Time Compilation**

> A Virtual Machine is a "computer inside of a computer", and thus bytecode is the native machine-level code for this computer inside a computer

**Just-in-Time Compiler**, part of the JVM, detects frequently used pieces of code (e.g., functions) during runtime and converts them to *native machine-level code to the compute machine's processor* (e.g., ARM or x86)
- A frequently used set of code is called **hot code**
- "cold code" or less frequently used code is just the JVM interpretting and executing the bytecode
- JIT Compilers is a huge reason why Java is known for its high performance

Example:
- The JVM executes bytecode line-by-line
- The JIT notices that some function `frequentlyCalledFunction()` is being called a lot - and thus the JIT converts it to native machine-level code based on the machine's processor that the JVM is on
- Going forward, the JVM executes the native code version instead for higher performance (think running a game on native hardware vs emulation)

### Ecosystem
Being the most historically popular language that is still commonly used to this day; it also results in Java being *widely supported* and filled with useful and powerful *third-party libraries*. As such, if you use Java, you open the door to the most powerful set of tools for a programmer. **This is often the reason why Java is considered the most popular enterprise-grade language**.

For example:
- Many big data processing frameworks and services (e.g., Spark, Flink, and Kafka) are built on top of a JVM, and thus have the highest performance when ran on one
- Some languages are built to leverage the JVM and thus benefit from its features (e.g., Kotlin, Scala, etc.)

## How is a Java Program converted to Bytecode?
More details can be found in Chapter 10 (specifically classloading)

![java sourcode to bytecode](images/java%20sourcecode%20pipeline.png)

The Pipeline:
1. Write human-readable Java code (`.java`)
2. `javac` program converts the Java Sourcecode into Java Bytecode (`.java` -> `.class`)
3. The JVM takes the bytecode then interprets and executes it
    - JVM will look for the entrypoint (`main()`)
    - The JIT Compiler comes into play here to identify "hot code" and converts it to native machine-code during runtime

### javac
**javac** is the standard Java compiler that translates .java source files into .class bytecode files. Although it doesn’t produce machine code directly, it is still considered a true compiler — it just targets a virtual machine (JVM) rather than physical hardware.
The JIT compiler in the JVM later converts this bytecode into machine code at runtime.

However **javac** is still considered _a compiler_, but just know that the resulting `.class` file is bytecode, not machine code

## Java vs Python
### Comparison
#### Differences:
|Java|Python|
|----|------|
|Compiled language (`.java` -> `.class` -> machine code)|Interpreted language|
|Statically typed|Dynamically typed|
|Object-oriented with functional programming features|Procedural language with support for OOP and functional programming|
| True multithreading with native threads and concurrency APIs | Multithreading via `threading` module, but **limited by the Global Interpreter Lock (GIL)** in CPython |
| Used for concurrent servers, high-performance backends       | More suited to I/O-bound concurrency using `asyncio` or multiprocessing for CPU-bound tasks            |
| Encapsulated by `{}` | Tab-based |


#### Similarities
- Both use bytecode

### Compiled Language vs Interpeted Language
| **Compiled Languages**                                        | **Interpreted Languages**                                              |
| ------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Translated to binary (machine code) **before execution**      | Executed **line-by-line at runtime**                                   |
| Typically **faster** and more optimized                       | Typically **slower** due to interpretation overhead                    |
| Platform-dependent (binary targets a specific OS/CPU)         | More platform-independent (runs with interpreter)                      |
| Harder to debug (must recompile)                              | Easier to debug (REPLs, immediate feedback)                            |
| Used for performance-critical systems (e.g., games, OS tools) | Used for flexibility and quick development (e.g., scripts, automation) |

A compiled language can be optimized in advance, but often requires heavier execution environments (and runtime environments) to do so. A interpretted language is often easier to understand and to get setup

# Chapter 2
> This chapter explains the Java programming language in detail, including Java 8 features, serving as both a reference for experienced developers (especially those familiar with C/C++) and a learning resource for beginners when paired with an introductory text.

*For personal purposes; this sections summary will only contain notes on non-trival syntaxual differences*

## General Syntaxual Commentary


## Other Loop Types (aside from `while` and `for`)
### `do while`

## `synchronize`

## `assert`

## Defining a Method
### Method Signatures
### Method Modifiers
### Variable-Length Argument Lists

## Classes and Objects

## Java Lambda Function / Expression

## Arrays
- Cloneable

## Reference Types vs Primitive Types
## Boxing
## Packages and Java Namespace
## Importing Rules
## Source File Structure
## Running a Java File



# Chapter 3

# Chapter 4

# Chapter 5

# Chapter 6

# Chapter 7

# Chapter 8

# Chapter 9

# Chapter 10

# Chapter 11

# Chapter 12

# Chapter 13
