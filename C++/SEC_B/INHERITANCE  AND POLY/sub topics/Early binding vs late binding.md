### **Early Binding in C++**

**Early binding** (also called **static binding** or **compile-time binding**) refers to the process where the method call is resolved at **compile time**, meaning the function to be invoked is determined when the code is compiled, not at runtime. This is the default behavior in C++ for **non-virtual functions**.

### Key Points:

1. **Compile-time Resolution**:
    
    - The compiler determines which function to call based on the type of the object at **compile time**.
    - For non-virtual functions, the method to be called is resolved based on the type of the **reference** or **pointer** that is used at compile time.
2. **Occurs in Non-Polymorphic Calls**:
    
    - Early binding occurs for **non-virtual** functions because the compiler knows exactly which function to call based on the type of the object.
    - In other words, for a non-virtual function, C++ directly links the call to a specific method based on the **object's static type** (the type defined in the code).
3. **Faster Execution**:
    
    - Since the function call is determined at compile time, there is no runtime overhead for function dispatch. This can make early binding faster than dynamic binding.

---

### Example of Early Binding:

Let’s look at an example with a **non-virtual** function to demonstrate **early binding**.

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    void show() {
        cout << "Base class show function" << endl;
    }
};

class Derived : public Base {
public:
    void show() {
        cout << "Derived class show function" << endl;
    }
};

int main() {
    Base baseObj;
    Derived derivedObj;
    
    baseObj.show();  // Calls Base's show function
    derivedObj.show();  // Calls Derived's show function

    return 0;
}
```

### **Explanation**:

1. In this example, both `Base` and `Derived` have their own version of the `show()` function.
2. The `show()` function is **not virtual**, so the function calls are resolved at compile time.
3. The compiler directly binds the calls to `baseObj.show()` and `derivedObj.show()` to the respective `show()` functions in the `Base` and `Derived` classes.

Here, **early binding** is at work because the compiler can directly resolve which version of the `show()` function to call for each object based on its **static type** (`Base` or `Derived`).

### Output:

```
Base class show function
Derived class show function
```

### **How Early Binding Works**:

- The function calls (`baseObj.show()` and `derivedObj.show()`) are resolved at compile time based on the **actual type** of the object (`baseObj` is of type `Base` and `derivedObj` is of type `Derived`).
- For `baseObj.show()`, the compiler knows it must call the `Base::show()` function.
- For `derivedObj.show()`, the compiler knows it must call the `Derived::show()` function.

Since there is no **virtual function** mechanism involved, the **binding is determined at compile time**, which is the essence of early binding.

---

### **Contrast with Late Binding (Dynamic Binding)**

While **early binding** happens at compile time, **late binding** (also called **dynamic binding**) happens at **runtime**.

Late binding is typically used with **virtual functions**. The function to be called is determined at runtime based on the **actual object type** (not the type of the pointer/reference used to call the method). This is what enables **polymorphism** in C++.

Here's an example of **late binding** using a virtual function:

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void show() {
        cout << "Base class show function" << endl;
    }
};

class Derived : public Base {
public:
    void show() override {
        cout << "Derived class show function" << endl;
    }
};

int main() {
    Base* ptr;
    Derived derivedObj;
    
    ptr = &derivedObj;
    ptr->show();  // Calls Derived's show function due to late binding (polymorphism)

    return 0;
}
```

### **Explanation of Late Binding**:

- Here, `show()` is a **virtual function**.
- The call to `ptr->show()` is resolved at **runtime**, based on the actual type of the object `ptr` is pointing to. Even though `ptr` is of type `Base*`, it points to a `Derived` object, so the **Derived** version of `show()` is called.

---

### **Summary**:

- **Early Binding (Static Binding)** occurs when function calls are resolved at **compile time**.
- It happens with **non-virtual functions** and is typically faster because there’s no runtime overhead.
- The function called is determined based on the **static type** of the object.
- **Late Binding (Dynamic Binding)** happens at **runtime** and is used with **virtual functions** to achieve **polymorphism**.

Let me know if you need more clarification or examples!