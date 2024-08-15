# Object-Oriented Programming Concepts in Java

## 1. Class and Object

**Description:** 
- **Class:** A blueprint or template for creating objects, defining their data and behavior.
- **Object:** An instance of a class, representing a specific implementation of the class blueprint.

**Purpose:** 
- **Class:** Provides a structure for organizing code and defining the properties and methods.
- **Object:** Represents real-world entities with attributes and behaviors, making the code modular and reusable.

**How to Achieve:** Define a class using the `class` keyword and create objects using the `new` keyword.

**Example:**
```java
class Car {
    String brand;
    String model;
    int year;

    void start() {
        System.out.println("Car is starting");
    }
}

// Usage
Car myCar = new Car();
myCar.brand = "Toyota";
myCar.model = "Corolla";
myCar.year = 2020;
myCar.start(); // Outputs: Car is starting
```
## 2. Inheritance
**Description:** Allows a class to inherit fields and methods from another class, creating a parent-child relationship.

**Purpose:** Promotes code reusability and logical hierarchy.

**How to Achieve:** Use the `extends` keyword to inherit from a superclass and override methods to provide specific behavior.

**Example:**
```java
class Vehicle {
    void start() {
        System.out.println("Vehicle starts");
    }
}

class Car extends Vehicle {
    void honk() {
        System.out.println("Car honks");
    }
}

// Usage
Car car = new Car();
car.start(); // Inherited method
car.honk();  // Own method
```
## 3. Abstraction

**Description:** Hides the complex reality and exposes only the necessary parts.

**Purpose:** Reduces complexity and isolates the impact of changes in the code.

**How to Achieve:** Use `abstract` classes or `interfaces` to define abstract methods that must be implemented by subclasses.

**Example:**
```java
interface Shape {
    void draw();
}

class Circle implements Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a circle");
    }
}

// Usage
Shape shape = new Circle();
shape.draw(); // Outputs: Drawing a circle
```
## 4. Polymorphism

**Description:** Allows objects to be treated as instances of their parent class rather than their actual class.

**Purpose:** Provides flexibility and the ability to define a common interface for different objects.

**How to Achieve:** Implement method overriding to provide specific implementations for subclasses and method overloading to handle different parameters.

**Example:**
```java
class Animal {
    void makeSound() {
        System.out.println("Animal makes sound");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("Cat meows");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Dog barks");
    }
}

// Usage
Animal myCat = new Cat();
Animal myDog = new Dog();
myCat.makeSound(); // Outputs: Cat meows
myDog.makeSound(); // Outputs: Dog barks
```
## 5. Encapsulation

**Description:** Bundles data and methods that manipulate the data within a class, hiding the internal state from outside.

**Purpose:** Protects data integrity and prevents unauthorized access.

**How to Achieve:** Declare fields as `private` and provide `public` getter and setter methods to access and modify them.

**Example:**
```java
class Account {
    private double balance;

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
}

// Usage
Account account = new Account();
account.deposit(100);
System.out.println(account.getBalance()); // Outputs: 100
```
## 6. Aggregation

**Description:** Models a "has-a" relationship between classes where the lifetime of the contained objects is independent of the container.

**Purpose:** Represents ownership without a strong dependency between the container and its parts.

**How to Achieve:** Define a class with references to other classes; the contained objects can be passed into the class.

**Example:**
```java
import java.util.ArrayList;
import java.util.List;

class Department {
    private List<Employee> employees = new ArrayList<>();

    void addEmployee(Employee employee) {
        employees.add(employee);
    }

    List<Employee> getEmployees() {
        return employees;
    }
}

class Employee {
    String name;
    // Additional details and methods
}

// Usage
Department department = new Department();
Employee employee = new Employee();
employee.name = "John Doe";
department.addEmployee(employee);
System.out.println(department.getEmployees().get(0).name); // Outputs: John Doe
```
## 7. Composition

**Description:** Represents a "part-of" relationship where the contained objects are created and destroyed along with the container object.

**Purpose:** Ensures that parts are inseparable from the whole, creating a strong dependency.

**How to Achieve:** Instantiate the contained objects within the constructor of the container class.

**Example:**
```java
class House {
    private Room room;

    House() {
        this.room = new Room();
    }

    void enter() {
        room.openDoor();
    }
}

class Room {
    void openDoor() {
        System.out.println("Room door opened");
    }
}

// Usage
House house = new House();
house.enter(); // Outputs: Room door opened
```
