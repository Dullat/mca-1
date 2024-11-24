**Code extensibility** and **code reusability** are two important principles in software development that help improve the maintainability and scalability of your codebase. These concepts are especially relevant in Object-Oriented Programming (OOP), where design patterns and OOP principles can help make code more flexible and reusable.

### 1. **Code Extensibility**
   **Extensibility** refers to the ability to extend or add new functionality to a software system without having to modify existing code. This is important because it allows a program to evolve and adapt to new requirements over time.

   In OOP, **inheritance** and **polymorphism** are key tools for achieving extensibility.

   - **Inheritance** allows you to create new classes that extend existing functionality.
   - **Polymorphism** allows you to override or extend methods in derived classes, providing new behaviors without changing the original code.

#### Example of Code Extensibility Using Inheritance and Polymorphism:
```cpp
#include <iostream>
using namespace std;

// Base class
class Shape {
public:
    virtual void draw() {
        cout << "Drawing a shape." << endl;
    }
    virtual ~Shape() = default; // Virtual destructor for proper cleanup
};

// Derived class
class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing a circle." << endl;
    }
};

// Another derived class
class Rectangle : public Shape {
public:
    void draw() override {
        cout << "Drawing a rectangle." << endl;
    }
};

// Function to use polymorphism
void displayShape(Shape* shape) {
    shape->draw();  // Calls the appropriate draw() function based on the actual object type
}

int main() {
    Shape* shape1 = new Circle();
    Shape* shape2 = new Rectangle();

    // Extending functionality without modifying Shape class
    displayShape(shape1);  // Output: Drawing a circle.
    displayShape(shape2);  // Output: Drawing a rectangle.

    delete shape1;
    delete shape2;

    return 0;
}
```

#### How it demonstrates extensibility:
- You can easily add new types of shapes (e.g., `Triangle`, `Square`, etc.) by creating new derived classes from `Shape`, without changing the original `Shape` class or the `displayShape` function.
- This allows the program to be extended to handle new types of shapes without modifying existing code.

### 2. **Code Reusability**
   **Reusability** refers to the ability to use existing code in different parts of the program or even in different projects. In OOP, code reuse is achieved through **inheritance**, **composition**, and **polymorphism**. Classes and methods can be written in such a way that they can be used in a variety of contexts without duplicating code.

#### Example of Code Reusability Using Inheritance:
```cpp
#include <iostream>
using namespace std;

// Base class (Reusable component)
class Vehicle {
public:
    void startEngine() {
        cout << "Starting engine..." << endl;
    }
    void stopEngine() {
        cout << "Stopping engine..." << endl;
    }
};

// Derived class 1
class Car : public Vehicle {
public:
    void drive() {
        cout << "Driving the car!" << endl;
    }
};

// Derived class 2
class Boat : public Vehicle {
public:
    void sail() {
        cout << "Sailing the boat!" << endl;
    }
};

int main() {
    // Car and Boat both reuse the Vehicle class
    Car car;
    Boat boat;

    car.startEngine();   // Reusing startEngine() from Vehicle class
    car.drive();         // Specific to Car
    car.stopEngine();    // Reusing stopEngine() from Vehicle class

    boat.startEngine();  // Reusing startEngine() from Vehicle class
    boat.sail();         // Specific to Boat
    boat.stopEngine();   // Reusing stopEngine() from Vehicle class

    return 0;
}
```

#### How it demonstrates reusability:
- The `Vehicle` class provides common functionality (like `startEngine()` and `stopEngine()`) that can be reused by any class representing a vehicle (such as `Car` and `Boat`).
- Both `Car` and `Boat` classes inherit from `Vehicle` and reuse its functionality without having to implement it again.
- This promotes **DRY** (Don't Repeat Yourself) by allowing code reuse, which makes your program smaller and easier to maintain.

### Code Reusability with Composition (Alternative to Inheritance):
Composition is another technique for promoting reusability. Instead of using inheritance, you can create classes that contain instances of other classes and delegate functionality to them.

#### Example of Code Reusability Using Composition:
```cpp
#include <iostream>
using namespace std;

// Class representing an Engine
class Engine {
public:
    void start() {
        cout << "Engine started." << endl;
    }
    void stop() {
        cout << "Engine stopped." << endl;
    }
};

// Class representing a Car
class Car {
private:
    Engine engine; // Composing the Car class with an Engine instance
public:
    void start() {
        engine.start();  // Reusing Engine's functionality
        cout << "Car is moving." << endl;
    }
    void stop() {
        engine.stop();  // Reusing Engine's functionality
        cout << "Car has stopped." << endl;
    }
};

int main() {
    Car myCar;
    myCar.start();  // Output: Engine started. Car is moving.
    myCar.stop();   // Output: Engine stopped. Car has stopped.

    return 0;
}
```

#### How it demonstrates reusability:
- The `Engine` class is reused by the `Car` class through composition. Instead of inheriting from `Engine`, the `Car` class has an instance of `Engine` and uses it to start and stop the car.
- This way, `Engine` can be reused across different types of vehicles (such as `Truck`, `Motorcycle`, etc.) without the need for inheritance.

### Summary of Extensibility and Reusability:

1. **Extensibility**:
   - Achieved using **inheritance** (to add new functionality to existing classes) and **polymorphism** (to change or extend behavior).
   - Allows you to add new features to a program without modifying the original code.

2. **Reusability**:
   - Achieved using **inheritance** (to reuse code from base classes) and **composition** (by including instances of reusable objects).
   - Helps avoid code duplication and promotes cleaner, more maintainable code.

In conclusion, **extensibility** allows your code to grow without breaking existing functionality, and **reusability** ensures that your code is modular and can be used in different contexts with minimal changes. Both of these principles are vital for building scalable and maintainable software.