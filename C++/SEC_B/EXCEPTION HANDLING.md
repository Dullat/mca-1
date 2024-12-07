[Exception Handling in C++ - GeeksforGeeks](https://www.geeksforgeeks.org/exception-handling-c/)


## simple exception
```cpp
#include <iostream>
class MyException{
    public:
    std::string s;
    MyException(std::string msg){
        s = msg;
    }
    
    std::string getMsg(){
        return s;
    }
};
int main() {
    try{
        int a = 0;
        if(a == 0){
            throw MyException("no division with 0");
        }
    }catch(MyException& e){
        std::cout<<e.getMsg();
    }

    return 0;
}
```


---
Let's dive into **exception handling** in C++, covering the following topics:

1. **Catching Class Types (including Derived Class Exceptions)**
2. **Handling Derived Class Exceptions**
3. **Catching Exceptions**
4. **Restricting Exceptions**
5. **Rethrowing Exceptions**
6. **`terminate()` and `unexpected()` Exceptions**
7. **Uncaught Exceptions**

---

### 1. **Catching Class Types (Catching Base and Derived Class Exceptions)**

In C++, when an exception is thrown, you can catch the exception using **base class pointers or references**. You can catch **both base and derived class exceptions** by properly using inheritance in your exception classes.
### 2. **Handling Derived Class Exceptions**

When catching exceptions in a hierarchy, make sure to catch the derived class **before** catching the base class to avoid ambiguity.

## example for both

```cpp
#include <iostream>
class MyException{
    public:
    std::string s;
    MyException(std::string msg){
        s = msg;
    }
    
    virtual std::string getMsg(){
        return s;
    }
};

class DrivedEx : public MyException{
    public:
    std::string a;
    DrivedEx(std::string x):MyException(x){
        a = x;
    }
    
    std::string getMsg(){
        return a;
    }
};

int main() {
    try{
        int a = 0;
        if(a == 0){
            throw DrivedEx("no division with 0");
        }
    }catch(DrivedEx& e){  // drived
        std::cout<<e.getMsg();
    }catch(MyException& e){   // base
        std::cout<<e.getMsg();
    }

    return 0;
}
```



---

### 3. **Catching Exceptions**

You can catch specific exceptions and handle them appropriately. The `catch` block can specify the exception type.

#### Example: Catching Different Exception Types

```cpp
#include <iostream>
#include <stdexcept>  // For std::exception
using namespace std;

int main() {
    try {
        throw runtime_error("Runtime error occurred");
    }
    catch (const runtime_error& e) {
        cout << "Caught runtime_error: " << e.what() << endl;
    }
    catch (const exception& e) {  // Catch base class exception for all standard exceptions
        cout << "Caught exception: " << e.what() << endl;
    }

    return 0;
}
```

### **Explanation:**

- Here, we catch a specific `runtime_error` exception, and if we didn't catch it, the base class `exception` would catch it.
- We can catch multiple exceptions in sequence.

### **Output:**

```
Caught runtime_error: Runtime error occurred
```

---

### 4. **Restricting Exceptions (No Exceptions)**

You can specify that certain functions **do not throw exceptions** by using the `noexcept` keyword. This can help optimize code and clarify intent.

#### Example: Restricting Exceptions with `noexcept`

```cpp
#include <iostream>
using namespace std;

void myFunction() noexcept {  // Function declared as noexcept (no exceptions allowed)
    cout << "This function does not throw exceptions!" << endl;
}

int main() {
    try {
        myFunction();
    }
    catch (...) {  // Catch any exception
        cout << "An exception occurred!" << endl;
    }

    return 0;
}
```

### **Explanation:**

- `noexcept` ensures that the function `myFunction` cannot throw any exceptions. If it tries to, a `std::terminate()` is invoked.
- If `noexcept`-declared functions do throw exceptions, it results in undefined behavior.

### **Output:**

```
This function does not throw exceptions!
```

---

### 5. **Rethrowing Exceptions**

Sometimes, after catching an exception, you may want to handle it in some way but then **rethrow** it for further handling at a higher level.

#### Example: Rethrowing Exceptions

```cpp
#include <iostream>
using namespace std;

void functionA() {
    try {
        throw runtime_error("Error in functionA");
    }
    catch (const exception& e) {
        cout << "Caught exception in functionA: " << e.what() << endl;
        throw;  // Rethrow the caught exception
    }
}

int main() {
    try {
        functionA();
    }
    catch (const exception& e) {
        cout << "Caught exception in main: " << e.what() << endl;
    }

    return 0;
}
```

### **Explanation:**

- Inside `functionA`, we catch the exception, print a message, and then **rethrow** the exception using `throw;`.
- The exception is caught again in `main()`.

### **Output:**

```
Caught exception in functionA: Error in functionA
Caught exception in main: Error in functionA
```

---

### 6. **`terminate()` and `unexpected()` Exceptions**

- **`terminate()`**: If a function marked `noexcept` throws an exception, or if an uncaught exception propagates out of a `catch` block, the program will terminate by calling `std::terminate()`.
- **`unexpected()`**: This is called when a function throws an exception that is not listed in its exception specification (though this is deprecated in modern C++).

#### Example: `terminate()` in Action

```cpp
#include <iostream>
#include <exception>
using namespace std;

void myFunction() noexcept {
    throw runtime_error("Error in myFunction");
}

int main() {
    try {
        myFunction();  // This will call std::terminate because myFunction is noexcept
    }
    catch (...) {
        cout << "This will never be printed." << endl;
    }

    return 0;
}
```

### **Explanation:**

- The function `myFunction` is declared as `noexcept`, but it throws an exception, so it triggers `std::terminate()`, and the program terminates immediately.

### **Output:**

```
Program terminated due to an uncaught exception.
```

---

### 7. **Uncaught Exceptions**

If an exception is thrown and not caught by any `catch` block, the program terminates by calling **`std::terminate()`**.

#### Example: Uncaught Exception

```cpp
#include <iostream>
#include <string>
using namespace std;

class MyException {
public:
    std::string msg;
    MyException(std::string m) : msg(m) {}
};

int main() {
    try {
        // Throw an exception
        throw MyException("This is an uncaught exception");
    }
    // Notice no catch block to handle the exception here!
    
    // Program continues executing (which it won't if exception is uncaught)
    cout << "Program continues..." << endl;

    return 0;
}

```

### **Explanation:**

- The exception is thrown but never caught, so `std::terminate()` is invoked, and the program ends.

### **Output:**

```
Program terminated due to an uncaught exception.
```

---

### **Summary of Key Concepts:**

1. **Catching Class Types**: You can catch exceptions of base or derived classes, and base class references or pointers will catch derived class exceptions.
2. **Handling Derived Class Exceptions**: Catch derived class exceptions **before** base class exceptions to avoid ambiguity.
3. **Catching Exceptions**: You can catch specific exceptions and use multiple `catch` blocks for different types.
4. **Restricting Exceptions**: Use `noexcept` to restrict functions from throwing exceptions.
5. **Rethrowing Exceptions**: Use `throw;` to rethrow an exception after catching it, allowing higher-level handlers to process it.
6. **`terminate()` and `unexpected()`**: These are invoked when an exception is thrown in `noexcept` functions or when an unexpected exception is encountered.
7. **Uncaught Exceptions**: Uncaught exceptions cause the program to terminate.

---

Let me know if you need further clarification or examples!