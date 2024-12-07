[Templates in C++ with Examples - GeeksforGeeks](https://www.geeksforgeeks.org/templates-cpp/)

Great! Let's move on to **Templates** in C++ — this is a very powerful feature that allows you to write **generic code**, which works with any data type.

We'll cover the following:

1. **Generic Functions (Function Templates)**
2. **Generic Classes (Class Templates)**
3. **Template Function Overloading**

---
```cpp
#include <iostream>
template <typename t>
class abc{
    public:
    t a;
};

template <typename M>
M printShit(M x){
    return x + 1;
}

int main() {
    abc<int> a1;
    a1.a = 12;
    std::cout << a1.a;
    std::cout<< printShit(12);

    return 0;
}
```
### 1. **Generic Functions (Function Templates)**

A **function template** allows you to define a function that can work with **any data type** without having to write the same function multiple times for different types.

#### Syntax of Function Template:

```cpp
template <typename T>
T add(T a, T b) {
    return a + b;
}
```

- `template <typename T>`: This is the declaration of the template. `T` is a placeholder for any data type.
- `T add(T a, T b)`: The function `add` will work with any data type `T`.

### Example:

```cpp
#include <iostream>
using namespace std;

// Function template to add two numbers of any type
template <typename T>
T add(T a, T b) {
    return a + b;
}

int main() {
    cout << add(10, 20) << endl;      // Calls add<int>(int, int)
    cout << add(10.5, 20.3) << endl;  // Calls add<double>(double, double)
    return 0;
}
```

### **Explanation:**

- The `add` function works for both `int` and `double` types because of the template.
- When you call `add(10, 20)`, the compiler generates a version of the function specifically for `int`. Similarly, for `add(10.5, 20.3)`, a version for `double` is generated.

### **Output:**

```
30
30.8
```

---

### 2. **Generic Classes (Class Templates)**

A **class template** allows you to create a class that works with any data type.

#### Syntax of Class Template:

```cpp
template <typename T>
class Box {
private:
    T value;
public:
    Box(T val) : value(val) {}
    T getValue() {
        return value;
    }
};
```

- `template <typename T>`: This tells the compiler to treat `T` as a placeholder for any type when creating the class.
- `T value`: The class has a data member `value` of type `T`.

### Example:

```cpp
#include <iostream>
using namespace std;

// Class template to store a value of any type
template <typename T>
class Box {
private:
    T value;
public:
    Box(T val) : value(val) {}
    T getValue() {
        return value;
    }
};

int main() {
    Box<int> intBox(10);        // Box for int
    Box<double> doubleBox(10.5); // Box for double

    cout << intBox.getValue() << endl;   // 10
    cout << doubleBox.getValue() << endl; // 10.5

    return 0;
}
```

### **Explanation:**

- `Box<int>` creates an object of type `Box` where `T` is replaced by `int`.
- Similarly, `Box<double>` creates an object where `T` is replaced by `double`.
- You can create `Box` objects for any type, and the class functions will work with that type.

### **Output:**

```
10
10.5
```

---

### 3. **Template Function Overloading**

You can **overload** template functions the same way you overload normal functions, but with templates, you can define multiple versions of a function template based on different types or parameters.

#### Example of Template Function Overloading:

```cpp
#include <iostream>
using namespace std;

// Template function to add two values of the same type
template <typename T>
T add(T a, T b) {
    return a + b;
}

// Overloaded template function to add two values of different types
template <typename T, typename U>
auto add(T a, U b) -> decltype(a + b) {  // Return type deduced using decltype
    return a + b;
}

int main() {
    cout << add(10, 20) << endl;      // Calls add<int, int>(int, int)
    cout << add(10.5, 20) << endl;    // Calls add<double, int>(double, int)
    cout << add(10, 20.5) << endl;    // Calls add<int, double>(int, double)
    cout << add(10.5, 20.5) << endl;  // Calls add<double, double>(double, double)
    return 0;
}
```

### **Explanation:**

- The first `add` function works for two parameters of the **same type** (`T`).
- The second `add` function is overloaded and works for two parameters of **different types** (`T` and `U`). We use `decltype(a + b)` to deduce the return type based on the result of adding `a` and `b`.

### **Output:**

```
30
30.5
30.5
31
```

- The function selects the correct template based on the types of the arguments passed to it.
- If the arguments are of the same type, the first version is called. If the arguments are of different types, the overloaded version is called.

---

### Summary of Concepts:

- **Function Templates**: Allow you to write functions that work with any data type.
- **Class Templates**: Allow you to create classes that can handle any data type.
- **Template Function Overloading**: Allows you to have multiple versions of the same function template, based on different argument types.

This way, templates enable **code reusability** and make your programs more **generic** and flexible. Let me know if you need further clarification or examples!