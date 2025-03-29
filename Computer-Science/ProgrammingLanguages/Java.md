# The fundamnetals of Java 

## 1. Objects and Classes

an object is real-world entity represented in code. Everything in java is built around objects. A car object has properties (color, speed) and hevaiors (accelerate(), break()). 
An object is an instance of a class. 

A class is a blueprint for creating objects. It defines:
* Fields (attributes): the data the object is holding
* Methods (behaviors): the acions/logic the object can perform. 
  
Example: 
```Java
public class Car {
    // Fields (attributes)
    String color;
    int speed;

    // Constructor (special method that creates objects)
    public Car(String color, int speed) {
        this.color = color;
        this.speed = speed;
    }

    // Method (behavior)
    public void accelerate() {
        speed += 10;
    }
}
```
Now we can create car objects: 
```java
Car myCar = new Car("Red", 50);
myCar.accelerate();  // Increases speed by 10
```

## 2. Primitive vs Reference Types

Primitive data types store simple values directly in memory. 
For instance: 
Type	Size	Example	Description
byte	8-bit	byte b = 100;	Stores small integers (-128 to 127).
short	16-bit	short s = 32000;	Stores medium-sized integers (-32,768 to 32,767).
int	32-bit	int x = 100;	Most common integer type.
long	64-bit	long bigNum = 1000000L;	Stores large integers.
float	32-bit	float f = 3.14f;	Stores decimals with lower precision.
double	64-bit	double d = 3.141592653;	Stores high-precision decimals.
boolean	1-bit	boolean flag = true;	Stores true or false.
char	16-bit	char letter = 'A';	Stores a single character.

Reference types: 
Objects, strings, arrays and custom classes are reference types. 
They store memory addresses rather than actual values. 

Examples and differences:
```Java
String name = "Alice";   // Reference to a String object
Car myCar = new Car("Blue", 60);  // Reference to a Car object
```
Differences:
* primative stores actual data (int x = 10; stores 10 in memory)
* Objects stores memory address (Car myCar = new Car(); stores the location of the object in memory.)

## 3. variables, Fields, and Scope. 

### Types of variables:

1. Local variables: declared inside a method, only used inside of that method.
2. Instance variables (fields) - declared in a class, unique to each object.
3. Class variables (static fields) - shared by all objects of a class. 

Example: 
```Java
public class Person {
    // Instance variable (each object has its own name)
    private String name;

    // Static variable (shared among all Person objects)
    private static int count = 0;

    public Person(String name) {
        this.name = name;
        count++;  // Increments global counter
    }

    public static int getCount() {
        return count;  // Static method accessing static field
    }
}
```
Usage:
```Java
Person p1 = new Person("Alice");
Person p2 = new Person("Bob");

System.out.println(Person.getCount()); // Prints: 2 (static field shared)
```

Scope: 
* Local variables: Exist oly inside the method they are declared in.
* Instance variables (fields): exist as long as the object exists.
* Class variables (static fields): exist as long as the program is running. 
  
## 4. Strings in Java: 

A string is an immutable object (cannot be changed post creation). 
```java
String s1 = "hello"; // String literal (efficient)
String s2 = new String("hello"); // Creates a new object
```
### Common string methods:
```java
String str = "Hello, World!";
System.out.println(str.length());        // 13
System.out.println(str.charAt(0));       // 'H'
System.out.println(str.substring(7, 12)); // "World"
System.out.println(str.toLowerCase());   // "hello, world!"
System.out.println(str.toUpperCase());   // "HELLO, WORLD!"
System.out.println(str.startsWith("He")); // true
System.out.println(str.endsWith("!"));   // true
```

### Looping thru a string: 
```java
for (int i = 0; i < str.length(); i++) {
    System.out.println(str.charAt(i));
}
```

### **Core Logic & Operator Behavior in Java**
Understanding **operator precedence, associativity, and evaluation order** is key to writing correct Java code. Let's go over important rules that govern Java's core logic.

---

## **1. Operator Precedence & Associativity**
Java follows a strict **precedence order** when evaluating expressions. If multiple operators appear in an expression, **precedence determines what gets evaluated first**, and **associativity determines how operators of the same precedence are evaluated**.

### **Operator Precedence Table (Highest to Lowest)**
| Precedence | Operators | Associativity |
|------------|------------|------------------|
| **1** (Highest) | `()`, `[]`, `.`, `::` (Method reference) | Left-to-Right |
| **2** | `++` (post), `--` (post) | Left-to-Right |
| **3** | `++` (pre), `--` (pre), `+` (unary), `-` (unary), `~`, `!` | Right-to-Left |
| **4** | `*`, `/`, `%` | Left-to-Right |
| **5** | `+`, `-` | Left-to-Right |
| **6** | `<<`, `>>`, `>>>` (Bitwise shift) | Left-to-Right |
| **7** | `<`, `<=`, `>`, `>=`, `instanceof` | Left-to-Right |
| **8** | `==`, `!=` | Left-to-Right |
| **9** | `&` (Bitwise AND) | Left-to-Right |
| **10** | `^` (Bitwise XOR) | Left-to-Right |
| **11** | `|` (Bitwise OR) | Left-to-Right |
| **12** | `&&` (Logical AND) | Left-to-Right |
| **13** | `||` (Logical OR) | Left-to-Right |
| **14** | `?:` (Ternary Operator) | Right-to-Left |
| **15** | `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `&=`, `|=`, `^=`, `<<=`, `>>=`, `>>>=` | Right-to-Left |
| **16** (Lowest) | `,` (Comma Operator) | Left-to-Right |

### **Associativity Rule**
- **Left-to-Right Associativity:** Operators are evaluated **from left to right** when they have the same precedence.
- **Right-to-Left Associativity:** Operators like `=` and `?:` are evaluated **right to left**.

---

## **2. Expression Evaluation Examples**
### **Example 1: Multiplication vs. Addition**
```java
int x = 10 + 2 * 5;
System.out.println(x); // 20
```
**Why?**
- `*` has a **higher precedence** than `+`, so `2 * 5` evaluates first (`10`).
- Then `10 + 10` evaluates, resulting in `20`.

### **Example 2: Left Associativity in Arithmetic**
```java
int x = 100 / 5 / 2;
System.out.println(x); // 10
```
**Why?**
- `/` is left-associative, so it's evaluated **from left to right**:
  - `(100 / 5) = 20`
  - `(20 / 2) = 10`

### **Example 3: Right Associativity in Assignment**
```java
int a, b, c;
a = b = c = 5; 
System.out.println(a + " " + b + " " + c); // 5 5 5
```
**Why?**
- `=` is **right-associative**, so it's evaluated as:
  - `c = 5` → `c` is assigned `5`
  - `b = c` → `b` gets `5`
  - `a = b` → `a` gets `5`

### **Example 4: Logical AND vs. Bitwise AND**
```java
boolean result = true & false;   // Bitwise AND
boolean result2 = true && false; // Logical AND
System.out.println(result);  // false
System.out.println(result2); // false
```
**Key Difference:**
- `&` (Bitwise AND) evaluates **both** sides always.
- `&&` (Logical AND) **short-circuits** if the first operand is `false`.

---

## **3. Short-Circuiting Behavior**
- `&&` (Logical AND) and `||` (Logical OR) support **short-circuit evaluation**.
- If the first operand determines the result, Java **does not evaluate** the second operand.

### **Example: Logical AND Short-Circuit**
```java
int a = 5;
if (a > 10 && ++a > 0) {  // `++a` is NEVER executed
    System.out.println("Condition met");
}
System.out.println(a); // Still 5
```
- Since `a > 10` is `false`, Java **skips** evaluating `++a`.

### **Example: Logical OR Short-Circuit**
```java
int b = 5;
if (b < 10 || ++b > 0) {  // `++b` is NEVER executed
    System.out.println("Condition met");
}
System.out.println(b); // Still 5
```
- Since `b < 10` is `true`, Java **ignores** `++b > 0`.

---

## **4. Operator Overloading (Not in Java)**
Unlike C++:
- Java **does not** allow operator overloading.
- `+` is the only operator that is overloaded **for strings**:
  ```java
  System.out.println("Hello " + "World"); // Hello World
  ```
  Here, `+` performs **string concatenation**, not arithmetic.

---

## **5. Ternary Operator and Nested Ternary**
The ternary operator (`?:`) is **right-associative**.

### **Example: Simple Ternary**
```java
int a = 10, b = 20;
int min = (a < b) ? a : b;
System.out.println(min); // 10
```

### **Example: Nested Ternary**
```java
int x = 5, y = 10, z = 15;
int min = (x < y) ? (x < z ? x : z) : (y < z ? y : z);
System.out.println(min); // 5
```
- `(x < y) ? (x < z ? x : z) : (y < z ? y : z)` → Nested evaluation.

---

## **6. Bitwise vs. Logical Operators**
| **Operator** | **Type** | **Behavior** |
|-------------|---------|--------------|
| `&` | Bitwise AND | Evaluates **both** sides |
| `&&` | Logical AND | **Short-circuits** (doesn't evaluate right side if left is `false`) |
| `|` | Bitwise OR | Evaluates **both** sides |
| `||` | Logical OR | **Short-circuits** (doesn't evaluate right side if left is `true`) |

### **Example: Difference Between `&` and `&&`**
```java
boolean a = true, b = false;
System.out.println(a & b);  // false (Both sides are evaluated)
System.out.println(a && b); // false (b is **not** evaluated)
```

---

## **7. Modulo (`%`) Behavior**
Modulo (`%`) gives **remainder**, but it follows **sign rules**.

### **Example: Negative Modulo**
```java
System.out.println(-10 % 3);  // -1
System.out.println(10 % -3);  // 1
System.out.println(-10 % -3); // -1
```
- Sign of the remainder **follows the dividend** (`a % b → sign of a`).

---

### **Final Thoughts**
- **Operator precedence** controls what gets evaluated first.
- **Associativity** decides how operators of the same precedence group.
- **Short-circuiting** helps optimize performance (`&&` and `||`).
- **Right-associative assignment (`=`)** lets you chain assignments.
- **Bitwise and logical operators are different** (`&` vs. `&&`).

Mastering these concepts helps you **debug tricky expressions and optimize code**.
