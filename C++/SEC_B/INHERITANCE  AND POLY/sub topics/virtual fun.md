### 2. **Virtual Functions and Run-Time Polymorphism**

#### **Why Virtual Functions?**

better option : [Virtual Function in C++ - GeeksforGeeks](https://www.geeksforgeeks.org/virtual-function-cpp/)

A **virtual function** in a base class allows derived classes to provide their own implementation of that function, even when it's called via a pointer or reference to the base class. This is a key feature of **dynamic polymorphism**.

In C++, virtual functions work by using a **vtable (virtual table)** behind the scenes. The vtable allows the program to look up the function to call at runtime, based on the actual object type, rather than the type of the pointer/reference used.

#### **Key Points About Virtual Functions:**

- Declared using the `virtual` keyword in the base class.
- When a base class pointer or reference calls a virtual function, C++ ensures that the correct function from the derived class is called (if it's overridden).
- **Destructor** should be virtual in the base class if you plan to delete derived objects through a base class pointer to ensure proper cleanup.

### 3. **Example: Virtual Functions and Polymorphism**

Let’s look at an example where we define a base class `Shape` and derived classes `Circle` and `Rectangle`, each with an overridden `draw()` function.

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    // Virtual function
    virtual void draw() {
        cout << "Drawing a Shape" << endl;
    }

    // Virtual destructor (important when using polymorphism)
    virtual ~Shape() {
        cout << "Shape destroyed" << endl;
    }
};

class Circle : public Shape {
public:
    void draw() override {  // Function overriding
        cout << "Drawing a Circle" << endl;
    }

    ~Circle() {
        cout << "Circle destroyed" << endl;
    }
};

class Rectangle : public Shape {
public:
    void draw() override {  // Function overriding
        cout << "Drawing a Rectangle" << endl;
    }

    ~Rectangle() {
        cout << "Rectangle destroyed" << endl;
    }
};

int main() {
    // Create objects
    Shape* shape1 = new Circle();    // Base class pointer to derived object
    Shape* shape2 = new Rectangle(); // Base class pointer to another derived object

    shape1->draw();  // Will call Circle's draw() due to polymorphism
    shape2->draw();  // Will call Rectangle's draw() due to polymorphism

    delete shape1; // Calls Circle's destructor
    delete shape2; // Calls Rectangle's destructor

    return 0;
}
```

#### **Explanation:**

- `Shape` has a virtual `draw()` method.
- Both `Circle` and `Rectangle` override this method.
- The function that gets called (either `Circle::draw` or `Rectangle::draw`) depends on the actual object type, not the pointer type. This is **run-time polymorphism** in action.
- When `delete` is called on the pointers (`shape1` and `shape2`), the destructors of `Circle` and `Rectangle` are properly invoked because the base class destructor is virtual. This ensures proper cleanup of resources when polymorphism is involved.

---
- **Pure Virtual Functions**: If a virtual function in the base class is meant to be overridden in derived classes but doesn’t provide a default implementation, it can be made **pure virtual**. This turns the base class into an **abstract class** (i.e., you cannot instantiate it).
    

```cpp
class Shape {
public:
    virtual void draw() = 0;  // Pure virtual function
    virtual ~Shape() = default;  // Destructor can be defaulted
};
```

#### **Example: Pure Virtual Function**

```cpp
class Shape {
public:
    virtual void draw() = 0;  // Pure virtual function
    virtual ~Shape() = default;  // Virtual destructor
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing a Circle" << endl;
    }
};

int main() {
    // Shape shape; // Error: Cannot instantiate abstract class
    Shape* s = new Circle();
    s->draw();  // Calls Circle's draw
    delete s;
    return 0;
}
```
