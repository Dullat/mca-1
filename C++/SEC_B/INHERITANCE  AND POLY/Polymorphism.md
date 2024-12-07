### **1. Polymorphism in C++**
https://www.geeksforgeeks.org/cpp-polymorphism/

**Polymorphism** allows us to call the same function on different objects, but each object may respond in a different way based on its type. It’s a key feature of **Object-Oriented Programming (OOP)** that allows for flexibility and reusability of code.

There are two types of polymorphism in C++:
- **Compile-time polymorphism** (also known as **static polymorphism**)
- **Run-time polymorphism** (also known as **dynamic polymorphism**)

Let’s start with **run-time polymorphism**, which is achieved through **virtual functions**.


---
Since we already discussed function overriding and inheritance, we'll focus more on **run-time polymorphism** here, particularly through the use of **virtual functions**.


### 4. **Key Details and Nuances**

- **Overriding vs Hiding**: When a derived class defines a function with the same signature as the base class function but without `virtual`, it's considered a **function hiding** rather than overriding.
    
    - To properly override, always use the `virtual` keyword in the base class.
- **Virtual Destructor**: A virtual destructor ensures that when an object of a derived class is deleted through a base class pointer, the derived class's destructor is called first, followed by the base class's destructor. Without a virtual destructor, this can result in memory leaks or undefined behavior.
    

### 5. **Summary of Polymorphism with Virtual Functions:**

- Virtual functions enable **run-time polymorphism**, allowing a program to determine the correct method to call based on the actual object type, not the pointer/reference type.
- This is crucial for designing flexible systems that can work with different types of derived objects via a common base class.
- Always use a **virtual destructor** in the base class to ensure proper cleanup when objects are deleted polymorphically.

---

## Question : so polymorhism is basically using virtual functions like calling base class's fun with drived object with base memory?

# ANS:-

Yes, you're on the right track! Polymorphism in C++ is fundamentally about **using base class pointers or references** to call **derived class functions**, with the actual function called being determined at **runtime** (thanks to **virtual functions**).

### **What is Polymorphism?**

Polymorphism allows a single function or method to behave differently based on the object that invokes it. In C++, **polymorphism** is primarily achieved using **virtual functions** and **inheritance**.

### **Key Concept:**

- **Base class pointer/reference** can point to an object of the **derived class**, and when calling a **virtual function** on that base class pointer/reference, the **derived class's version** of the function gets called.

This is possible because the **virtual function mechanism** ensures that the correct function is called based on the **actual object type** (i.e., the type of the object the pointer/reference is pointing to), not the type of the pointer/reference itself.

### **In Simple Terms:**

- **Polymorphism** allows you to **call a derived class function** via a **base class pointer** or **reference**, even though you may not know the exact derived class type at compile time.
- This happens only if the function is **virtual** in the base class.

### **Example of Polymorphism (using Virtual Functions):**

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {   // Virtual function
        cout << "Base class show function" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {  // Overriding the base class show function
        cout << "Derived class show function" << endl;
    }
};

int main() {
    Base* ptr;       // Base class pointer
    Derived derived; // Derived class object
    ptr = &derived;  // Base class pointer pointing to derived object
    
    ptr->show();  // Calls Derived's show due to polymorphism
    return 0;
}
```

### **Key Points from the Code**:

1. **Base class pointer (`Base* ptr`)** is used to point to a **Derived class object**.
2. The `show()` function is **virtual** in the base class. This means that the function call is **polymorphic**: it will call the **Derived class's** version of `show()` even though `ptr` is a **Base class pointer**.
3. The **actual function to be called** is determined at **runtime** based on the **type of the object** (`Derived` in this case).

### **Output**:

```
Derived class show function
```

### **How Does This Work?**

- **Virtual function** mechanism: When you define a function as `virtual` in the **base class**, C++ uses a **vtable (virtual table)** behind the scenes. The vtable is a table of function pointers. For each object of a class, C++ maintains a pointer to the vtable, and when a virtual function is called, the corresponding function pointer is looked up in the vtable and called.
- **Polymorphism** allows the **same function name** to invoke different behavior based on the **object type** (base or derived).

---

### **In Summary**:

- **Polymorphism** allows using **base class pointers/references** to call functions of derived classes.
- This is only possible when the function is declared **virtual** in the base class.
- The function to be called is determined at **runtime** (this is **late binding** or **dynamic binding**).
- It enables the use of a **base class interface** to interact with **derived class objects** in a flexible and reusable way.

So yes, **polymorphism** is essentially about calling a **base class function** using a **derived class object** and having the **derived class version** of the function invoked, when the function is **virtual**.