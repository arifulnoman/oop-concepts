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
**Description:** Allows a class to inherit fields and methods from another class, creating a parent-child relationship. We should use inheritance only for is-a relationships.

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

## Types of Inheritance in Java
- **Single Inheritance**
- **Multilevel Inheritace**
- **Hierarchical Inheritance**
- **Multiple Inheritance**
- **Hybrid Inheritance**

### Single Inheritance:
A subclass inherits from one and only one superclass.

**Example:**

```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
```
### Multilevel Inheritance:
 A class is derived from a subclass, creating a hierarchy of classes.

Example:

```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}

class Puppy extends Dog {
    void play() {
        System.out.println("Puppy plays");
    }
}
```
### Hierarchical Inheritance:
 Multiple subclasses inherit from a single superclass.

Example:

```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    void meow() {
        System.out.println("Cat meows");
    }
}
```
### Multiple Inheritance (via Interfaces):
 A class inherits from multiple interfaces. This is the only form of multiple inheritance supported in Java, as it avoids the diamond problem.The diamond problem is a situation in object-oriented programming where a class inherits from two classes that have a common base class, leading to ambiguity in the method resolution.  

 Example: `Not Allowed in java`

```java
class A {
    void method() {
        System.out.println("Method in A");
    }
}

class B extends A {
    @Override
    void method() {
        System.out.println("Method in B");
    }
}

class C extends A {
    @Override
    void method() {
        System.out.println("Method in C");
    }
}

class D extends B, C { // This will cause a compile-time error in Java
    // Compiler error: class D cannot have multiple base classes
}

public class Main {
    public static void main(String[] args) {
        D d = new D();
        d.method(); // Ambiguous call due to conflicting method implementations
    }
}

```
`Solution: `
```java
interface A {
    void method();
}

interface B extends A {
    @Override
    default void method() {
        System.out.println("Method in B");
    }
}

interface C extends A {
    @Override
    default void method() {
        System.out.println("Method in C");
    }
}

class D implements B, C {
    @Override
    public void method() {
        // Provide a specific implementation to resolve ambiguity
        System.out.println("Method in D");
    }
}

public class Main {
    public static void main(String[] args) {
        D d = new D();
        d.method(); // Outputs: Method in D
    }
}

```
### Hybrid Inheritance (Through Interfaces):
A combination of two or more types of inheritance. This is achieved in Java using interfaces to mix multiple inheritance types.

Example:

```java
interface Carnivore {
    void hunt();
}

class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal implements Carnivore {
    void bark() {
        System.out.println("Dog barks");
    }

    @Override
    public void hunt() {
        System.out.println("Dog hunts");
    }
}
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

**Description:** Allows objects to be treated as instances of their parent class rather than their actual class. Polymorphism enables a single action to behave differently based on the object.

**Purpose:** Provides flexibility and the ability to define a common interface for different objects. It allows methods to do different things based on the object it is invoked on, enhancing code reusability and maintainability.

**How to Achieve:**

1. **Method Overriding (Run-Time Polymorphism):** Subclasses provide a specific implementation of a method that is already defined in their superclass. The method that is called is determined at runtime based on the object's actual class.

2. **Method Overloading (Compile-Time Polymorphism):** Multiple methods with the same name but different parameters within the same class. The method that is called is determined at compile time based on the method's signature.

### Types of Polymorphism

#### 1. **Run-Time Polymorphism (Method Overriding)**

**Definition:** The method that is called is determined at runtime based on the actual object type. This is achieved through method overriding.

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
public class Main {
    public static void main(String[] args) {
        Animal myCat = new Cat();
        Animal myDog = new Dog();
        myCat.makeSound(); // Outputs: Cat meows
        myDog.makeSound(); // Outputs: Dog barks
    }
}
```
#### 2. **Compile-Time Polymorphism (Method Overloading)**

**Definition:** The method is determined at compile time based on the method signature (name and parameters). This is achieved through method overloading.

**Example:**
```java
class Calculator {
    // Method with one parameter
    int add(int a) {
        return a + 10;
    }

    // Method with two parameters
    int add(int a, int b) {
        return a + b;
    }

    // Method with three parameters
    int add(int a, int b, int c) {
        return a + b + c;
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(5));         // Outputs: 15
        System.out.println(calc.add(5, 10));     // Outputs: 15
        System.out.println(calc.add(5, 10, 15)); // Outputs: 30
    }
}
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
## 6. Association

**Description:** Defines a relationship between two classes where one class uses or interacts with another. The lifetime of the associated objects is independent, meaning they can exist without each other.

**Purpose:** Represents general relationships between objects, without strong dependencies.

**Types of Association:**
1. **One-to-One:** One instance of a class is associated with one instance of another class.
2. **One-to-Many:** One instance of a class is associated with multiple instances of another class.
3. **Many-to-Many:** Multiple instances of a class are associated with multiple instances of another class.

### Example of ALL Association:

**Example:**
```java
import java.util.ArrayList;
import java.util.HashSet;
import java.util.List;
import java.util.Set;

class Student {
    private String name;
    private Set<Course> courses = new HashSet<>();
    private Department department;

    Student(String name) {
        this.name = name;
    }

    void enrollInCourse(Course course) {
        courses.add(course);
        course.addStudent(this); // Maintain the relationship on both sides
    }

    Set<Course> getCourses() {
        return courses;
    }

    String getName() {
        return name;
    }

    void setDepartment(Department department) {
        this.department = department;
    }

    Department getDepartment() {
        return department;
    }
}

class Course {
    private String title;
    private Set<Student> students = new HashSet<>();

    Course(String title) {
        this.title = title;
    }

    void addStudent(Student student) {
        students.add(student);
    }

    Set<Student> getStudents() {
        return students;
    }

    String getTitle() {
        return title;
    }
}

class Department {
    private String name;
    private List<Student> students = new ArrayList<>();

    Department(String name) {
        this.name = name;
    }

    void addStudent(Student student) {
        students.add(student);
        student.setDepartment(this); // Set the department for the student
    }

    List<Student> getStudents() {
        return students;
    }

    String getName() {
        return name;
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        // Create departments
        Department department1 = new Department("Computer Science");
        Department department2 = new Department("Mathematics");

        // Create students
        Student student1 = new Student("Alice");
        Student student2 = new Student("Bob");

        // Create courses
        Course course1 = new Course("Mathematics");
        Course course2 = new Course("Science");

        // Enroll students in courses
        student1.enrollInCourse(course1);
        student1.enrollInCourse(course2);
        student2.enrollInCourse(course1);

        // Assign students to departments
        department1.addStudent(student1);
        department2.addStudent(student2);

        // Print details
        System.out.println(student1.getName() + " is enrolled in: ");
        for (Course course : student1.getCourses()) {
            System.out.println(course.getTitle());
        }

        System.out.println(student1.getName() + " belongs to department: " + student1.getDepartment().getName());

        System.out.println(course1.getTitle() + " has the following students: ");
        for (Student student : course1.getStudents()) {
            System.out.println(student.getName());
        }

        System.out.println(department1.getName() + " has the following students: ");
        for (Student student : department1.getStudents()) {
            System.out.println(student.getName());
        }
    }
}
```  
## Explanation

### One-to-One Association:
- **Student to Department:** Each `Student` is associated with exactly one `Department`. This relationship is maintained by the `setDepartment` method in the `Student` class and the `addStudent` method in the `Department` class.

### One-to-Many Association:
- **Department to Students:** Each `Department` can have multiple `Students`, but each `Student` can belong to only one `Department`. This is illustrated by the `List<Student>` in the `Department` class.

### Many-to-Many Association:
- **Student to Courses:** Each `Student` can enroll in multiple `Courses`, and each `Course` can have multiple `Students`. This relationship is managed by the `Set<Course>` in the `Student` class and the `Set<Student>` in the `Course` class.

This example demonstrates all types of associations, showing how `Student`, `Course`, and `Department` interact with one another while maintaining the necessary relationships.  
## Association: (Aggregation and Composition)

### Aggregation

**Description:** Aggregation models a "has-a" relationship where the lifetime of the contained objects is independent of the container. The contained objects can exist independently of the container object.

**Purpose:** Represents ownership without a strong dependency between the container and its parts.

**How to Achieve:** Define a class with references to other classes. The contained objects can be passed into the class and can exist independently.

**Example:**
```java
import java.util.ArrayList;
import java.util.List;

class Department {
    private String name;
    private List<Student> students = new ArrayList<>();

    Department(String name) {
        this.name = name;
    }

    void addStudent(Student student) {
        students.add(student);
        student.setDepartment(this); // Maintain the relationship
    }

    List<Student> getStudents() {
        return students;
    }

    String getName() {
        return name;
    }
}

class Student {
    private String name;
    private Department department;

    Student(String name) {
        this.name = name;
    }

    void setDepartment(Department department) {
        this.department = department;
    }

    Department getDepartment() {
        return department;
    }

    String getName() {
        return name;
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        Department department = new Department("Computer Science");
        Student student = new Student("Alice");

        department.addStudent(student);

        System.out.println(student.getName() + " belongs to department: " + student.getDepartment().getName());
    }
}
```
### Composition

**Description:** Composition represents a "part-of" relationship where the contained objects are created and destroyed along with the container object. The contained objects are strongly dependent on the container object and do not exist independently.

**Purpose:** Ensures that parts are inseparable from the whole, creating a strong dependency between the container and its contained objects.

**How to Achieve:** Instantiate the contained objects within the constructor of the container class. The contained objects are tied to the lifecycle of the container object.

**Example:**
```java
class Computer {
    private CPU cpu;
    private RAM ram;

    Computer(String cpuModel, int ramSize) {
        this.cpu = new CPU(cpuModel);
        this.ram = new RAM(ramSize);
    }

    void start() {
        System.out.println("Computer starting...");
        cpu.boot();
        ram.load();
    }

    private class CPU {
        private String model;

        CPU(String model) {
            this.model = model;
        }

        void boot() {
            System.out.println("CPU (" + model + ") booting up");
        }
    }

    private class RAM {
        private int size;

        RAM(int size) {
            this.size = size;
        }

        void load() {
            System.out.println("RAM (" + size + "GB) loading");
        }
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        Computer myComputer = new Computer("Intel i7", 16);
        myComputer.start();
    }
}
```
