https://www.geeksforgeeks.org/inheritance-in-c/

---
Let’s dive deeper into the specifics of **inheritance** in C++, covering the following aspects:

1. **Defining Derived Classes**
2. **Inheriting Private Members**
3. **Types of Derivation**
4. **Function Redefining (Overriding)**
5. **Constructors in Derived Classes**
6. **Types of Inheritance**

---

### **1. Defining Derived Classes**

A **derived class** in C++ is a class that inherits properties and behaviors (methods) from a **base class**. The derived class can add its own data members and methods, or modify the inherited ones.

#### Syntax:

```cpp
class Base {
public:
    int baseVar;
    void baseFunction() { cout << "Base class function\n"; }
};

class Derived : public Base {  // Derived class inherits from Base
public:
    int derivedVar;
    void derivedFunction() { cout << "Derived class function\n"; }
};
```

In the example above, `Derived` is the derived class that inherits from `Base`. The derived class can access the public members of the base class, and it can also have its own members (`derivedVar`, `derivedFunction`).

---

### **2. Inheriting Private Members**

In C++, **private members** of a base class cannot be accessed directly from the derived class. However, **protected** members can be inherited and accessed by derived classes.

- **Private members** of the base class are **not accessible** directly in the derived class.
- **Protected members** can be accessed in the derived class, but not from outside the class (like private members).

#### Example:

```cpp
#include <iostream>
using namespace std;

class Base {
private:
    int privateVar;
protected:
    int protectedVar;
public:
    int publicVar;

    Base() : privateVar(10), protectedVar(20), publicVar(30) {}

    void showValues() {
        cout << "privateVar: " << privateVar << endl;
        cout << "protectedVar: " << protectedVar << endl;
        cout << "publicVar: " << publicVar << endl;
    }
};

class Derived : public Base {
public:
    void accessMembers() {
        // privateVar is not accessible
        // cout << "privateVar: " << privateVar << endl;  // Error

        // protectedVar is accessible
        cout << "protectedVar: " << protectedVar << endl;
        cout << "publicVar: " << publicVar << endl;
    }
};

int main() {
    Derived obj;
    obj.accessMembers();  // Will print protectedVar and publicVar
    return 0;
}
```

**Output**:
```
protectedVar: 20
publicVar: 30
```

---

### **3. Types of Derivation**

The types of derivation refer to how classes are inherited from base classes. In C++, there are several types of derivation depending on the access specifier used when inheriting from the base class.

#### **a) Single Inheritance**
A derived class inherits from a single base class.

```cpp
class Base { /* Base class */ };
class Derived : public Base { /* Derived class */ };
```

#### **b) Multiple Inheritance**
A derived class inherits from multiple base classes.

```cpp
class Base1 { /* Base1 */ };
class Base2 { /* Base2 */ };
class Derived : public Base1, public Base2 { /* Derived class */ };
```

#### **c) Multilevel Inheritance**
A derived class inherits from a base class, and another derived class inherits from that derived class.

```cpp
class Base { /* Base class */ };
class Derived1 : public Base { /* Derived class 1 */ };
class Derived2 : public Derived1 { /* Derived class 2 */ };
```

#### **d) Hierarchical Inheritance**
Multiple derived classes inherit from a single base class.

```cpp
class Base { /* Base class */ };
class Derived1 : public Base { /* Derived class 1 */ };
class Derived2 : public Base { /* Derived class 2 */ };
```

#### **e) Hybrid Inheritance**
A combination of two or more types of inheritance.

```cpp
class Base { /* Base class */ };
class Intermediate1 : public Base { /* Intermediate class 1 */ };
class Intermediate2 : public Base { /* Intermediate class 2 */ };
class Derived : public Intermediate1, public Intermediate2 { /* Derived class */ };
```

**Note**: Hybrid inheritance can lead to problems like the **diamond problem**. This is solved by **virtual inheritance** (discussed earlier).

---

### **4. Function Redefining (Overriding)**

In C++, function overriding is a way to define a method in the derived class that has the same signature as a method in the base class. This is used to provide a specific implementation for a derived class while still keeping the base class’s method.

When you override a base class function in a derived class, the base class function must be declared as **virtual** (for runtime polymorphism).

#### Example:

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() {
        cout << "Base class display function\n";
    }
};

class Derived : public Base {
public:
    void display() override {
        cout << "Derived class display function\n";
    }
};

int main() {
    Base* basePtr;
    Derived derivedObj;
    basePtr = &derivedObj;

    basePtr->display();  // Calls Derived's display() due to virtual function
    return 0;
}
```

**Output**:
```
Derived class display function
```

In this case, the `display()` function is overridden in the `Derived` class, and when called via a base class pointer, the **derived class** version is executed.

---

### **5. Constructors in Derived Classes**

When a derived class is instantiated, its constructor is called, and it also calls the constructor of the base class. If the base class has a parameterized constructor, you need to explicitly call it from the derived class constructor using an **initializer list**.

#### Example:

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    Base(int x) {
        cout << "Base class constructor, x = " << x << endl;
    }
};

class Derived : public Base {
public:
    Derived(int x, int y) : Base(x) {  // Calling base class constructor
        cout << "Derived class constructor, y = " << y << endl;
    }
};

int main() {
    Derived obj(10, 20);
    return 0;
}
```

**Output**:
```
Base class constructor, x = 10
Derived class constructor, y = 20
```

In the `Derived` class constructor, we use the **initializer list** to call the constructor of the `Base` class, passing the argument `x`.

---

### **6. Types of Inheritance**

We already touched upon the **types of derivation**, but here’s a summary of the different **types of inheritance** that describe the relationships between classes:

1. **Single Inheritance**: A class is derived from only one base class.
2. **Multiple Inheritance**: A class is derived from more than one base class.
3. **Multilevel Inheritance**: A class is derived from a derived class, forming a chain.
4. **Hierarchical Inheritance**: Multiple classes are derived from a single base class.
5. **Hybrid Inheritance**: A combination of two or more types of inheritance.

---

### **Key Takeaways**

- **Private members** of a base class are not accessible directly by derived classes, but **protected** members are.
- **Function overriding** in derived classes allows you to change the behavior of a function, especially when using virtual functions for polymorphism.
- **Constructors** in derived classes must call the base class constructor, and this can be done through the initializer list.
- The **types of inheritance** determine how the relationships between classes are formed (single, multiple, etc.).
- Proper use of **function overriding**, **virtual inheritance**, and **constructors** is essential for building clean and efficient class hierarchies in C++.

---

Feel free to ask for any clarifications or dive deeper into any of these topics!