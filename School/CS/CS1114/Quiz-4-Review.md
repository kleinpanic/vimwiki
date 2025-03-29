# Quiz 4 Review - Thursday 27 march. 

> Will be code-writing questions covering 06 Pictures and For-Each loops. 
> and 07 Aggregation, Strings, and More loops, and prior knowledge from 5. 

## Topics: 

* Strings
* Pictures (Images) and Pixels
* Numeric for loops
* loops over characters in a string
* common string methods
    * length()
    * charAt()
    * startsWith()
    * endsWith()
    * substring()
    * toLowerCase()
    * toUpperCase()
    * string Concatenation using +
* Aggregation (using a field to refer to another object)
* delegation (Implementating some or all of the behavior of a method on one object by calling a method on a second object)
* Method overriding (redefining a method in a subclass)
* Implmeneting the toString() method. 
  
### 1. Strings: 

String in java are Objects, not primitive types. Strings in java store sequences of characters. Because they are immutable, once a string object is created,it cannot be changed. Instead, any modification results in a new String object being created. 

### 1.1 String methods: 

Java provides various in-house methods (bloated ass language) to manipulate and analyze strings. 

#### 1.1.1.1: int length() method: 
* Returns the number of characters (chars) in the string.
* Example: 
```java 
String text = "Hello, world!";
int length = text.length();  // length is 13
```

#### 1.1.1.2: charAt(int index)
* Returns a character at a specified position (indexing starts at 0)
* Example:
```java
String text = "Hello";
char first = text.charAt(0);  // 'H'
char last = text.charAt(4);   // 'o'
```

#### 1.1.1.3: boolean startsWith(String Prefix)
* Checks if a string's first character begins with another character or compares if a string begins wih another string.
* Example: 
```java
String url = "https://example.com";
boolean isSecure = url.startsWith("https");  // true
```
#### 1.1.1.4: boolean endsWith(String suffix)
* Checks if a string ends with another string.
* Example:
```java
String filename = "document.pdf";
boolean isPDF = filename.endsWith(".pdf");  // true
```
#### 1.1.1.5: String substring(int start, int end)
* Extracts part of a string from start to end-1. (index starts at 0)
* Example:
```java
String word = "banana";
String part1 = word.substring(0, 3);  // "ban"
String part2 = word.substring(2, 5);  // "nan"
```
#### 1.1.1.6: string toLowerCase() & string toUpperCase()
* Converts the string o lower or upper case
* Example: 
```java
String name = "Ada Lovelace";
System.out.println(name.toUpperCase());  // "ADA LOVELACE"
System.out.println(name.toLowerCase());  // "ada lovelace"
``` 
#### 1.1.1.7: Concatenation(+ Operator)
* Joins to strings, or if joinign a string and any other variable type, it turns the other variable type into a string. 
* Example:
```java
String firstName = "Alan";
String lastName = "Turing";
String fullName = firstName + " " + lastName;  // "Alan Turing"
```
* Additionally, with chars and int addition, java automatically promotes the char to its corresponing ASCII (Or unicode) integer
* example:
```java
public class Main {
    public static void main(String[] args) {
        char a = 'A';  // 'A' has an ASCII value of 65
        int result = a + 1; // 'A' (65) + 1 = 66
        System.out.println(result);  // Output: 66
        System.out.println((char) result); // Output: 'B'
    }
}
```

#### 1.1.1.8: string substring(int start) method w/ one arguement
The substring(int start) method in java returns a new string that starts at the given start index, and continues to the end of the original string.
* example:
```java
String text = "HelloWorld";
String part = text.substring(5);
System.out.println(part); // "World"
```
Breakdown:
* Strings in java are immutable, meaning every time a string is modified, a new string object is created.
* substring(int start) calls the new String(value, start, count - start), where value is the character array of the original string, start is the starting index, and count is the length of the stating string.
* It does not create a completely new character array; instead, it references the same character array internally. 

In older java versions, substring() would share the original string's character array, but i Java 7+, it copies the substring into a new character array to avoid memory leaks. 

#### 1.1.1.9: int indexOf(char target)
Search for the specified character starting from the beginniing of the string and returns the position of the first occurrence, or -1 if its not found. 

#### 1.1.2.1: boolean equals(Object other)
checks to see if the two strings / two objects have the same content. Do not use == for strings or objects as they reference memory addresses not physic memory. 

#### 1.1.2.3: toString() method
Every java class inherits a toString method from java.lang.Object.
Example:
```java
class Car {
    String model;
    Car(String model) { this.model = model; }

    @Override
    public String toString() {
        return "Car model: " + model;
    }
}
```
Default, the toString() returns ClassName@HashCode. Overriding this method often improves output readability. 

### 1.2 Looping thru strings. 
Looping thru the characters of a stirng can be done using a for-loop (duh). 
```java
String text = "hello";
for (int i = 0; i < text.length(); i++) {
    char letter = text.charAt(i);
    System.out.println(letter);
}
```
Logical breakdown:
1. i = 0 is the start. Start at first letter.
2. i < text.length(). keep looping until all characters are visited.
3. i++: incriments i
4. charAt(i) prints the character at index i. 
   
## 2. Pictures and Pixels 

A pixel (picture element) is a tiny dot in an image. Each pixel contains three color components: 
* Red (0-255)
* Green (0-255)
* Blue(0-255)

Here’s your data formatted into a **Markdown table**:

### 2.1: the Pixel Class. 
This class allows us to read, and change specific pixel values. 

#### 2.1.1: Getting pixel info:
```java
Pixel pix = image.getPixel(0, 0);
int red = pix.getRed();  // Get red value (0-255)
int green = pix.getGreen();
int blue = pix.getBlue();
```

#### 2.1.2: Changing Pixel Colors:
```java
pix.setRed(255);   // Make the pixel fully red
pix.setGreen(0);
pix.setBlue(0);
```

#### 2.1.2: The complete pixel method and descriptions: 
| **Pixel Method**                              | **Description**                                               |
|-----------------------------------------------|---------------------------------------------------------------|
| `int getRed()`                                | Get the red intensity (an integer from 0-255)                 |
| `int getGreen()`                              | Get the green intensity (an integer from 0-255)               |
| `int getBlue()`                               | Get the blue intensity (an integer from 0-255)                |
| `void setRed(int)`                            | Set the red intensity to a value from 0-255                   |
| `void setGreen(int)`                          | Set the green intensity to a value from 0-255                 |
| `void setBlue(int)`                           | Set the blue intensity to a value from 0-255                  |
| `int getX()`                                  | Get the x coordinate where this pixel is located in the image |
| `int getY()`                                  | Get the y coordinate where this pixel is located in the image |
| `void setColor(int red, int green, int blue)` | Set all three color values at once                            |


### 2.2: The Picture Class
Represents an entire image. 

#### 2.2.1: Accessing Pixels
```java
Pixel corner = image.getPixel(0, 0);
corner.setRed(0);
corner.setGreen(0);
corner.setBlue(255); // Turn the pixel blue
```

#### 2.2.2: Looping thru all pixels:
to process an entire image, you can use a for-each loop.
for (Pixel pix : image.getPixels()) {
    pix.setRed(255); // Make all pixels red
}

#### 2.2.3: complete table method
### **Picture Methods**
| **Picture Method**                   | **Description**                                                                                                                                |
|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| `new Picture(String)`                | Use this constructor to create a `Picture` from an image file by providing the file name in double quotes                                     |
| `new Picture(int width, int height)` | Use this constructor to create a new, blank `Picture` with the specified dimensions                                                                                         |
| `int getWidth()`                     | Get the width of this image, in pixels                                                                                                                                                                                                 |
| `int getHeight()`                    | Get the height of this image, in pixels                                                                                                                                                                                                                                  |
| `Pixel getPixel(int x, int y)`       | Get the pixel at the specified location                                                                                                                                                                                                                                                                   |
| `Pixel[] getPixels()`                | Get all the pixels in the image in a form suitable for use in a for-each loop                                                                                                                                                                                                                                                              |
| `void show()`                        | Show this picture on the screen                                                                                                                                                                                                                                                                                                                                                                       |
| `void repaint()`                     | Update the on-screen image shown using `show()`                                                                                                                                                                                                                                                                                                                                                                                                |
| `void hide()`                        | Hide the image shown on the screen using `show()`                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `void explore()`                     | Show the image using an image explorer view that allows you to inspect the color of any pixel in the image                                                                                                                                                                                                                                                                                                                                                                                      |
| `void reload()`                      | If this image was loaded from a file, discard any changes and reload it fresh from the original file to restore its original appearance                                                                                                                                                                                                                                                                                                                                                                                 |

## 3. Loops:
Loops repeat a set of instructions under conditions. 

### 3.1: Numeric for loops.
A numeric for-loop is used when you know how many times the loop should run. 
```java
for (int i = 0; i < 10; i++) {
    System.out.println("Iteration: " + i);
}
```
Logic Breakdown: 
1. int i = 0: defines int i and sets it to 0. start at 0.
2. i < 10; true while i is less then 10.
3. i++ increase i by 1. 
   
### 3.2 For loops over strings: 
Strings are indexed 0 to length-1. 
```java
String word = "example";
for (int i = 0; i < word.length(); i++) {
    System.out.println(word.charAt(i));
}
```

### 3.3 For-Each loops.
a for-each loop is used to iterate over collections (arrays, lists)
```java
int[] numbers = {1, 2, 3, 4};
for (int num : numbers) {
    System.out.println(num);
}
```
Behind the scenes, it uses iterators. The java compiler rewrites the for-each loop as:
```java
for (int i = 0; i < numbers.length; i++) {
    int num = numbers[i];
}
```
This for each int num in collection numbers, and end at the end.

## 4. Agreegation (Objects Referencing Other Objects.)
Aggregation means one object contains another object as a field. 
Example: 
The car object contains an Engine reference and Engine exists indepenently of the Car object.
```java
class Engine {
    void start() { System.out.println("Engine started"); }
}

class Car {
    private Engine engine;
    Car(Engine engine) { this.engine = engine; }
}
```

## 5. Method Overriding
Overriding refers to a subclass redfning a method from its parent class. The syntax "requires" or expects an @Override flag. Not required.

Example:
```java
class Animal {
    void makeSound() { System.out.println("Some sound"); }
}

class Dog extends Animal {
    @Override
    void makeSound() { System.out.println("Bark"); }
}
```
Inside of the code, java checks method signatures, and it uses dynamic method dispatches to call the subclass version over the superclass version. 

## 6. Important Java Logic

### 6.1: Integer Division
In java, divison between two integers only keeps the whole number part (truncate the decimals). 
```java
int result = 5 / 2; //returns 2 not 2.5
```
Java does not round, but truncates towards zero. If one of the operands is a double, floating point division will occur
```java
double result = 5 / 2.0; //2.5
```
If both are int it uses integer division, if one is a double it promotes the int to a double and performs floating point division. 

### 6.2: Java Operators: 

#### 6.2.1: Arithmetic Operators (+,-,*,/,%)
```java
int x = 10, y = 3;
int sum = x + y;  // 13
int diff = x - y; // 7
int prod = x * y; // 30
int div = x / y;  // 3 (integer division) divides
int mod = x % y;  // 1 (remainder) - Returns the division remainder
int mod = mod++; // increment
int mod = mod--; //decrement
```

#### 6.2.2: Relational (Comparison Operators)
* == checks if two VARIABLES(simple) are equal.
* != means not equal
* > and < is greater then or less then
* >= <= is greater then or equal and less than or equal

#### 6.2.3: Logical Operators(&&, ||, !)
* && is and
* || is or
* ! is not 
  
#### 6.2.4: Bitwise Operators
These are operators on the binary level on indiviudal bits of an interger. These only work on integers (byte, short, int, long)
* & - Bitwise and - returns 1 if both bits are 1.
* ` - ` - bitwise OR.
* ^ - Bitwise XOR - Returns 1 if only one bit is 1
* ~ - Bitwise NOT - flips all bits (1 -> 0, 0->1)
* << - left shift - shifts bit left (multiples by 2^n)
* >> - right shift - shifts bit right (divides by 2^n)
* >>> - Unsigned right shift - Right Shifts without keeping sign bit
* <<< - Unsigned left shift - left shifts without keeping sign bit

```java
int a = 3; (0011)
a <<= 2;
system.out.println(a); // 12 (1100)
```


#### 6.2.5: Assignment Operators
* x+=n is the same as x=x+n
* x-=n is the same as x=x-n
* x*=n is the same as x=x * n
* x/=n is the same as x=x/n
* x%=n is the same as x=x%n
* x&=n is the same as x=x&n
* x|=n is the same as x=x|n
* x^=n is the same as x=x^n
* x>>=n is the same as x=x>>n
* x<<=n is the same as x=x<<n

#### 6.2.6: Ternary Operators (?)
The ternary operator is a shortcut for if-else. 

```java
condition ? value_if_true : value_if_false
```

Examples:
```java
int a = 10, b = 20;
int min = (a < b) ? a : b;
System.out.println(min);  // 10
```
is same as 
```java
int min;
if (a < b) {
    min = a;
} else {
    min = b;
}
```

### 6.3: Java Control flow:

Conditional Statements:
1. If-else statments:
```java
int age = 20;
if (age >= 18) {
    System.out.println("You are an adult.");
} else {
    System.out.println("You are underage.");
}
```

2. Switch Statement:
```java
int day = 3;
switch (day) {
    case 1: System.out.println("Monday"); break;
    case 2: System.out.println("Tuesday"); break;
    case 3: System.out.println("Wednesday"); break;
    default: System.out.println("Invalid day");
}
```

3. For loop:
```java
for (int i = 0; i < 5; i++) {
    System.out.println("Iteration: " + i);
}
```

4. While loop: 
```java
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}
```

6. Do-while loop
```
int i = 0;
do {
    System.out.println(i);
    i++;
} while (i < 5);
```

### 6.4: Java keywords:

Keyword	Purpose
static	Method/variable belongs to class instead of object
final	Prevents modification (constant variables, final methods/classes)
this	Refers to current object instance
super	Calls parent class method or constructor
break	Exits loop or switch-case
continue	Skips current loop iteration
return	Exits method and returns a value
throw	Throws an exception
implements	Implements an interface
extends	Inherits from a superclass

### 6.5: Java collections:
1. ArrayLists:
```java
import java.util.ArrayList;

ArrayList<String> list = new ArrayList<>();
list.add("Apple");
list.add("Banana");
System.out.println(list.get(0)); // Apple
```
2. HashMap
```java
import java.util.HashMap;

HashMap<String, Integer> map = new HashMap<>();
map.put("Alice", 30);
map.put("Bob", 25);
System.out.println(map.get("Alice")); // 30
```

### 6.6 Java Memory Management:
1. Stack: Method calls, local variables
2. Heap: Objects, instance variables
3. Garbage collection: Java auto removes unused objects with no references. 
   
### 6.7:Java classes and Objects and Constructors:
1. class and object:
```java
class Car {
    String brand;
    Car(String brand) { this.brand = brand; }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car("Toyota");
        System.out.println(myCar.brand);
    }
}
```
2. Constructors:
```java
class Car {
    String model;
    // Constructor
    public Car(String model) {
        this.model = model;
    }
}
```

### 6.8: Java Exception handling

Java has try and catch stateements and throws.
Return is used to send back a value from a method. Terminates execution of the method as well. 
Throw on the other hand is used to signal an error (exception) and stops the execution of the entire program immediately. 

## 7. Java.lang.object class
This is the superclass to all Java classes. It has import methods such as toString(), equals(Object obj), hashCode(), getClass(), and more. It defines basic object behavior, and provides polymorphism. 

## 8. Random Numbers
To generate a random number, use import student.utils.Random or java.utils.Random;. This provides a method called generator() to get an object that represents a random number generator. Here we only need to deal with generating random integers and the generator provdes a method that is very useful for this purpose. 
For student:
```java
Random generator = Random.generator();   // local variable to refer to the random number generator
int value = generator.nextInt(4);        // generate a random number from 0 - 3
```

The random class provides a method called nextInt() that generates a random integer. It takes a single parameter, which is an upper limit. When you provide this upper limit, the method will generatea number from 0(inclusive) up to (not inclusive) the upper limit. 

for java:
```java
import java.util.Random;
Random rand = new Random();
int num = rand.nextInt(10); // 0-9
```
Internally it uses a pseudo-random-numbe generator (PRNG) based on a seed. The default seed is the current time. 

## 9. Delegation
Delegation is when an object passes work onto another object. 
example:
Computer does not implement printing logic. It delegates it to the printer class / object. 

```java
class Printer {
    void print() { System.out.println("Printing..."); }
}

class Computer {
    private Printer printer;
    Computer(Printer printer) { this.printer = printer; }

    void startPrinting() {
        printer.print();  // Delegates work
    }
}
```
