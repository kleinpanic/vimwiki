# **Quiz 1 Review**

## **1. Objects and Classes**
### **Objects**
- An **object** is an instance of a class.
- Objects have **attributes** (characteristics) and **methods** (actions they can perform).
- Example: In the **Jeroo simulator**, a `Jeroo` object has:
  - **Attributes**: Position, direction, number of flowers.
  - **Methods**: `hop()`, `pick()`, `plant()`, etc.

### **Classes**
- A **class** is a blueprint for creating objects.
- A **Jeroo** class defines what a Jeroo is and what it can do.
- Example class definition:
  ```java
  public class Jeroo {
      // Attributes
      int flowers;
      String direction;
      
      // Methods
      public void hop() { /* Code to move forward */ }
  }
  ```
- An **object is created** from a class using `new`.

---

## **2. Methods and Calling Methods**
### **Methods**
- **Methods** define what an object can do.
- A **method call** executes an action for an object.
- Example:
  ```java
  jessica.hop();
  ```
  - Calls the `hop()` method for `jessica`, making the Jeroo move forward.

### **Writing Methods**
- A method is defined with a return type, name, and optional parameters.
- Example:
  ```java
  public void hopAndPlant() {
      this.hop();
      this.plant();
  }
  ```
  - `this.hop();` → Moves the Jeroo forward.
  - `this.plant();` → Plants a flower at the new position.

---

## **3. Creating New Objects Using `new`**
### **Instantiation**
- **Creating an object** uses the `new` keyword.
- Example:
  ```java
  Jeroo jessica = new Jeroo(8);
  ```
  - Creates a Jeroo named `jessica` with 8 flowers.

---

## **4. Inheritance: Superclass, Subclass, and `extends`**
### **What is Inheritance?**
- **Inheritance** allows a subclass to inherit attributes and methods from a superclass.
- **Superclass**: The base class that provides methods and attributes.
- **Subclass**: A class that extends another class and inherits its features.

### **Using `extends`**
- To create a subclass, use `extends`:
  ```java
  public class SmartJeroo extends Jeroo {
      public void hopAndPlant() {
          this.hop();
          this.plant();
      }
  }
  ```
  - `SmartJeroo` **inherits** all behaviors from `Jeroo` and **adds new methods**.

### **Superclass vs. Subclass**
| Concept        | Description                                                           |
|----------------|-----------------------------------------------------------------------|
| **Superclass** | Parent class that provides methods and attributes.                    |
| **Subclass**   | Child class that inherits from a superclass and can override methods. |
| **`extends`**  | Keyword that establishes inheritance.                                 |

---

## **5. Method Stubs**
- A **method stub** is a placeholder for a method, allowing code to compile before full implementation.
- Example:
  ```java
  public void hopAndPlant() {
      // TODO: Implement this method
  }
  ```
- **Why use stubs?** 
  - Allows you to **structure** a program before writing all logic.
  - Helps in **incremental development**.

---

## **6. Core Methods for LightBot**
LightBot understands **5 core movement methods**:
1. `move()`: Move forward one square.
2. `turnLeft()`: Turn 90° counterclockwise.
3. `turnRight()`: Turn 90° clockwise.
4. `jump()`: Jump forward over a block.
5. `turnLightOn()`: Light up a blue tile.

Example:
```java
andy.move();
andy.turnRight();
andy.jump();
andy.turnLightOn();
```
- Moves forward, turns, jumps, and lights up a blue tile.

---

## **7. Core Methods for Jeroo**
Jeroos understand **7 core methods**:

| Method            | Description                                     |
|-------------------|-------------------------------------------------|
| `hop()`           | Moves forward one space.                        |
| `hop(n)`          | Moves forward `n` spaces.                       |
| `pick()`          | Picks up a flower.                              |
| `plant()`         | Plants a flower.                                |
| `toss()`          | Throws a flower to disable a net.               |
| `turn(direction)` | Turns left or right.                            |
| `give(direction)` | Gives a flower to another Jeroo in a direction. |

### **Example Usage**
```java
jessica.hop(3);   // Move 3 spaces
jessica.pick();    // Pick a flower
jessica.turn(LEFT); // Turn left
jessica.toss();    // Toss a flower to disable a net
```

---

## **8. Class Hierarchy and Inheritance**
### **Hierarchy Structure**
- Java organizes classes into a **tree-like structure**.
- **Top-level class**: `Object` (every class extends from `Object`).
- **Example hierarchy**:
  ```
  Object
   ├── Island
   ├── Jeroo
       ├── SmartJeroo
  ```

### **Inheritance in Jeroos**
- **`Jeroo`** (Superclass) has standard methods like `hop()`, `pick()`, etc.
- **`SmartJeroo`** (Subclass) can override or add new methods.

Example:
```java
public class SmartJeroo extends Jeroo {
    public void hopTwice() {
        this.hop();
        this.hop();
    }
}
```
- `SmartJeroo` **inherits** all `Jeroo` methods and **adds** `hopTwice()`.

---

## **9. Polymorphism**
- **Polymorphism** means different objects can respond differently to the same method call.
- **Example**: 
  - A `Jeroo` and a `SmartJeroo` both have a `hop()` method, but `SmartJeroo` might override it.

```java
public class SmartJeroo extends Jeroo {
    @Override
    public void hop() {
        System.out.println("Smart Jeroo hops differently!");
    }
}
```
- If `SmartJeroo` objects are used, they execute the overridden `hop()`.

