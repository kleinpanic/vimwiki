# Overview of Java Language 

## High-Level Conceptual Overview

Java is a statically typed, object oriented, programming language originally developed by Sun Microsystems (now Oracle). It was designed with the philosophy of "write once, run anywhere," meaning code compiled on one machien should run on any device with a Java Virtual Machine installed. 

## Java Under the Hood (Architecture Overview)

### Source to Execution Flow 

- Java has a "Write Once, Run ANywhere" phiosphy, powered by the Java Virtual Machine (JVM). 
  
```text
Java Source Code (.java)
       ↓
Java Compiler (javac)
       ↓
Bytecode (.class)
       ↓
JVM (interprets or JIT compiles .class)
       ↓
Machine Code (via interpreter or JIT)
```

* Bytecode is a set of instructions understood by the JVM, not the hardware. 
  
### Compilation Pipeline: Source Code -> Machine Execution

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }
}
```

#### a. Compilation (.java -> .class)
* The `.java` file is compiled by the javac compiler into a `.class` file.
* The `.class` file contains Java Bytecode (Not Machine code!).

#### b. Bytecode:
* bytecode is a paltofrm independent intermeidate low level representation of the java code.
* IT is stack-based (unlike x86 which is register based). For example: 
  
```asm
0: getstatic     #2                  // Field java/lang/System.out:Ljava/io/PrintStream;
3: ldc           #3                  // String Hello, world!
5: invokevirtual #4                  // Method java/io/PrintStream.println:(Ljava/lang/String;)V
8: return
```

## The JVM (Java Virtual Machine)

The `.class` file is executed by the JVM, which acts as an abstract machine. Key responsibilities:

### a. Class Loader Subsystem

* Loads, links and initializes`.class` files
* Classloader Hierarchy:
    * Boostrap Loader: Loads core java Libraries.
    * Extension Loader
    * Application Loader

### b. Runtime Data Areas 

* Method Area: Class-level data like method info, static variables.
* Heap: All objects live here.
* Stack: Each thread gets its own stack (local vars, operand stack, etc.).
* Program Counter Register
* Native Method Stack: For interfacing with native libraries (JNI). 
  
### c. Execution Engine

Has two main modes:
* Interpreter: Executes bytecode line-by-line.
* JIT (Just-In-TIme) Compiler: Compiles frequently used bytecode (hot paths) into native machine code for speed.

### d. HotSpot JVM.

* Identifies "hot" methods or loops and compiles themto native code using:
    * C1 Compiler (Client) - Optimized for quick start.
    * C2 Compiler (Server) - Optimized for Long-Running Perofrmance. 
      
## Memory Management and Garbage Collection

### Java Heap Structure:

* Young Generations:
    * Eden Space: New Objects GO here.
    * Survivor Space (S0 & S1): Objects that survive GC are moved here.
* Old Generation: Long-lived objects.

### Garbage Collectors:

* Serial GC (Stop the world, single-threaded)
* Parallel GC (Multi-Threaded)
* CMS (Concurrent Mark-Sweep)
* G1 (Garbage First) - Default Now
* ZGC / Shenandoah - Low pause collectors for big heaps. 
  
## Access Modifiers 

| Modifier                | Access Scope                      |
| ----------------------- | --------------------------------- |
| `public`                | Everyone                          |
| `protected`             | Same class + subclasses + package |
| `default` (no modifier) | Package-private                   |
| `private`               | Only within same class            |

`protected` in java means that the member sits between private and public in Java's access-control ladder:
| Modifier        | Visible to …                                                                                                                   | Typical use                                                                                                 |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| `private`       | **Only** code in the *same class*                                                                                              | Encapsulate internal state                                                                                  |
| **`protected`** | 1. All classes in the **same package** (package‑private reach)  <br>2. **All subclasses** *everywhere*, even in other packages | Give subclasses controlled access to inherited state/behavior while still hiding it from the general public |
| (no modifier)   | All classes in the **same package**                                                                                            | Package‑scope helpers                                                                                       |
| `public`        | Everyone                                                                                                                       | API surface                                                                                                 |

### Why and When to Declare a Field `Protected`

* Subclass Customizations: Frankework / DSL Design often stores reusable, low-level state in a superclass (e.g., `x`, `y`, `width`, `height` in a GUI `Components`)
* Package Collaboration + Inheritance: Inside one pakcage, peer classes can stil lreach the field, but code in unrelated pakcages cannot unless its in a subclass.

Canonical Example:
```java
public class Shape {
    // accessible to subclasses and same‑package peers
    protected int x, y;         

    protected void move(int dx, int dy) {
        x += dx;
        y += dy;
    }
}

public class Circle extends Shape {
    private int radius;

    public void enlarge(int dr) {
        radius += dr;
        // direct access—allowed because x, y are protected
        System.out.printf("Center now at (%d,%d)%n", x, y);
    }
}
```


This gives you **Encapsulation**, a key principle of OOP. 

## Core OOP Concepts in Java

* Class = Blueprint
* Object = Instance
* Inheritance = Extends
* Polymorphism = Method overriding / Interfaces
* Encapsulation = Access Control
* Abstraction = Abstract Clases, Interfaces. 
  
Java supports single inheritace for classes, but multiple inheritance via interface. 

## Special Language Features: 

### a. Interfaces & Abstract Classes

* Interface: Only method signatures.
* Abstract Class: Can have both concrete and abstract methods. 
  
### b. Generics

* Type-safe containers: `List<String>` vs `List<Object>`
* Type erasure: generic type info is removed at runtime. 
  
### c. Annotations & Reflection

* Metadata like @Override, @Deprecated, @FunctionalInterface
* Type Erasure: Generic type info is removed at runtime. 
  
### d. Lambda Expressions (Java 8+)

* Functional Programming Support:
```java
list.forEach(e -> System.out.println(e));
```

### e. Streams API

* Pipeline for functional style operation:
```
list.stream()
    .filter(x -> x > 10)
    .map(x -> x * 2)
    .collect(Collectors.toList());
```

## JVM Language Interop

The JVM is not just for Java. Many languages compile down to Java Bytecode, such as: 
* Kotlin
* Scala
* Groovy
* Clojure
* JRuby
* Jython

This is because they all adhere to the JVM Spec. 

## Java vs Native Languages (C/C++)

| Feature               | Java            | C/C++                |
| --------------------- | --------------- | -------------------- |
| Memory Management     | GC              | Manual (malloc/free) |
| Platform Independence | Yes (JVM)       | No                   |
| Performance           | JIT-optimized   | Faster upfront       |
| Unsafe operations     | Hidden from dev | Fully exposed        |
| Interop               | JNI (clunky)    | Native               |
| Compilation           | Bytecode + JIT  | Native binary        |

## Under the Hood - MEthod Call Example 

A smple method call in Java undergoes:
1. Bytecode generation for `invokevirtual`, `invokestatic`, etc.
2. JVM method resolutions:
    * Constant Pool -> Method Address
    * Classloader Checks visibility
3. Frame Push on Stack
4. Execution or Native Code Dispatch (JIT)

## Build Systems & Packaging:

* `.class` files bundled into `.jar` (Java Archive) Files.
* Modern Tools:
    * Maven: XML-Based build + dependency Management
    * Gradle: Script based. 
      
### What is a jar file?

A `.jar` (Java Archive) is essentilly a zip file with a speicfic strucutre for Java Applications. It bundles togheter:
* Compiled `.class` Files
* Metadata (MANIFEST.MF)
* Resources(Images, config files, etc)

A Jar file distributes multiple classes in one file. Easier to deploy apps and libraries, and it can be executable if it includes a Main-Class entry in the manifest. 

## Bytecode into Machine Code 

Bytecode goes into machine code. Its handled at runtime by the JVM Execution Engine, using the Interpreter (Initial Execution) and the JIT Compiler (For Hot Code Paths). 

### Interpreter vs JIT Compiler 

#### Interpreter: 

* Reads and Executes the bytecode line by line.
* Slower than compilations, but faster startup.

#### Just-In-Time (JIT) Compiler

* Detects frequently used code ("Hot Spots").
* Converts Bytecode -> native machine code (x86, ARM, etc.)
* Caches the native code for future executions.

Results: JVM Optimizes as the program runs, blending portability with speed. 

Using java -XX:+UnlockDiagnosticVMOptions -XX:+PrintCompilation MyApp you can see JIT compilation in action. 

## Class, Instance, Static:

A class in java is a blueprint or template that defines:
* Fields
* Methods
* Constructors
* Nested Classes / Interfaces
* Access Modifies
Example:
```java
public class Dog {
    String name;
    static int totalDogs = 0;

    public Dog(String name) {
        this.name = name;
        totalDogs++;
    }

    public void bark() {
        System.out.println(name + " says woof!");
    }
}
```
Here: 
* a Dog is a class
* Each dog created with new Dog is an instance.
* totalDogs is a static variable shared across all Dog instances.

An instance is a real object created based on the class definition.
```java
Dog fido = new Dog("Fido");
Dog rex = new Dog("Rex");
```

* Fido and Rex are different instances.
* Each has their own name field.
* But they shared the static field totalDogs. 

In java, static means soemthing is tied to the class, ot to an instance of that class. 
The static keyword modifies:
* Variables
* Methods
* Blocks
* Nested Classes

Static = Belongs to the class, not to the instance.
| Type         | Scope                       |
| ------------ | --------------------------- |
| `static`     | Belongs to the class itself |
| `non-static` | Belongs to the instance     |

Static Variables: 
* One copy per class not per instance:
```java
static int totalDogs;
```

Static Method:
* Can be called without an instance of that class.
* Cannot access instance (this) members.
```java
public static void printTotalDogs() {
    System.out.println("Dogs: " + totalDogs);
}
```
> This will not return an error because totalDogs is a static varable. Not dereferncing a null pointer. 

### Static and its changes to the bytecode:

```java
public class Test {
    static int x = 5;
    int y = 10;

    public static void main(String[] args) {
        System.out.println(x);
    }
}
```

This gets turned into the Bytecode:
```asm
0: getstatic     #2 // Field Test.x:I
3: invokevirtual #3 // Method println
6: return
```
Explanation:
* `getstatic` is used to fetch a tatic field from the class (not from an object)
* Non static fields use `aload_0` (aka load this) then getfield.
| Accessing field | Bytecode Instruction              |
| --------------- | --------------------------------- |
| `Test.x`        | `getstatic Test.x`                |
| `this.y`        | `aload_0`, then `getfield Test.y` |

### Static vs Instance 

#### `static` field:
```java
public static int value = 42;
```
-> JVM stores this in the method area as part of the class's metadata.

#### `instance` field:
```java
public int value = 42;
```
-> stored in the **heap** as part of the object instance. 

On the machine code level, JIT treats `static` field and method like globals (single address per class) whereas instance members are accessed via memory offsets related to the `this` pointer (like structs in C). 
```java
Dog d = new Dog("Fido");
d.bark();          // needs object pointer to resolve
Dog.printInfo();   // no object required
```
The JIT-Compiled Native Code Will:
* Optimize `static` methods like simple function calls (no virtual dispatch)
* It uses virutal table dispatch or memory offsets for instance methods. 
  
### Summary

| Feature          | Static                                   | Instance                               |
| ---------------- | ---------------------------------------- | -------------------------------------- |
| Belongs to       | Class                                    | Object                                 |
| Stored in        | Method Area                              | Heap                                   |
| Access via       | `ClassName.member`                       | `object.member`                        |
| Bytecode         | `getstatic`, `putstatic`, `invokestatic` | `aload_0`, `getfield`, `invokevirtual` |
| Native code      | Global-like, no indirection              | Object pointer + offset dereferencing  |
| Requires object? | No                                       | Yes                                    |


