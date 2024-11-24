Let's move on to **destructors**! Destructors are a crucial part of object-oriented programming in C++ because they help manage resources and clean up when an object goes out of scope or is explicitly destroyed.

### **1. Destructor Properties**

A **destructor** is a special member function that is called when an object is destroyed. It is used to perform cleanup tasks, such as releasing memory or closing file handles.

#### Key Properties of Destructors:
- **Name**: A destructor has the same name as the class, but it is preceded by a tilde (`~`). For example, if the class is `MyClass`, the destructor will be `~MyClass()`.
- **No return type**: Destructors do not have a return type, not even `void`.
- **No parameters**: Destructors cannot take parameters, so they cannot be overloaded.
- **Automatic Invocation**: A destructor is automatically called when an object goes out of scope or is explicitly deleted. You cannot call a destructor manually like a regular function.
- **One per class**: A class can only have one destructor, because it can't be overloaded (no parameters).
- **Called when an object is destroyed**: When an object goes out of scope (local objects) or is deleted (dynamically allocated objects), the destructor is called.

### **2. Destructor's Role**
Destructors are primarily used for **resource deallocation**, like:
- Releasing **dynamically allocated memory** (using `delete`).
- Closing **file handles** or network connections.
- Releasing other resources that need explicit cleanup.

If an object allocates memory using `new` (or other resources like file handles), the destructor ensures that these resources are freed to prevent **memory leaks**.

### **3. Destroying Objects (Automatic and Manual Deletion)**

#### **Automatic Destruction**
- **Local objects**: When a local object goes out of scope (i.e., when the function finishes), its destructor is automatically called.
  
  **Example:**
  ```cpp
  class MyClass {
  private:
      int* ptr;
  
  public:
      MyClass() {
          ptr = new int(10);  // Dynamically allocated memory
          cout << "Constructor called" << endl;
      }
  
      ~MyClass() {
          delete ptr;  // Cleanup memory
          cout << "Destructor called" << endl;
      }
  };

  int main() {
      MyClass obj;  // Constructor is called here
      // Destructor will automatically be called when obj goes out of scope
      return 0;
  }
  ```

  **Output:**
  ```
  Constructor called
  Destructor called
  ```

- **Static and Global Objects**: Static and global objects are destroyed at the end of the program, and their destructors are called then.

#### **Manual Deletion (Dynamic Objects)**
For objects created dynamically with `new`, you can explicitly destroy them using `delete`, which will invoke the destructor.

**Example:**
```cpp
class MyClass {
private:
    int* ptr;

public:
    MyClass() {
        ptr = new int(20);  // Dynamically allocated memory
        cout << "Constructor called" << endl;
    }

    ~MyClass() {
        delete ptr;  // Free dynamically allocated memory
        cout << "Destructor called" << endl;
    }
};

int main() {
    MyClass* obj = new MyClass();  // Constructor called
    delete obj;  // Destructor is called manually here
    return 0;
}
```

**Output:**
```
Constructor called
Destructor called
```

### **4. Rules for Constructors and Destructors**
Understanding the rules governing constructors and destructors is crucial for proper resource management in C++.

#### **A. Constructor and Destructor Relationship**
- **Constructors and destructors are automatically paired**: When an object is created, the constructor is called. When the object is destroyed (goes out of scope or is explicitly deleted), the destructor is called automatically.
- **The order of calling**: When an object is created, the constructor is called first. When the object is destroyed, the destructor is called last.
  
#### **B. Rule #1: A Destructor Should Match the Constructor**
- If a constructor allocates resources dynamically (e.g., memory with `new`), the **destructor must deallocate** that memory (using `delete`) to avoid memory leaks.
  
#### **C. Rule #2: Destructor Is Not Inherited**
- Unlike constructors, **destructors are not inherited**. However, a derived class destructor will **automatically call the destructor of the base class**.
- If the base class destructor is not declared as `virtual`, deleting a derived class object through a pointer to the base class will lead to undefined behavior because the base class destructor will be called, but the derived class destructor will not.

#### **Example: Virtual Destructor for Safe Deletion**
If you have polymorphism (base class pointer to derived class object), you must declare the base class destructor as `virtual` to ensure proper cleanup.

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    Base() {
        cout << "Base Constructor called" << endl;
    }

    // Virtual destructor
    virtual ~Base() {
        cout << "Base Destructor called" << endl;
    }
};

class Derived : public Base {
public:
    Derived() {
        cout << "Derived Constructor called" << endl;
    }

    ~Derived() {
        cout << "Derived Destructor called" << endl;
    }
};

int main() {
    Base* obj = new Derived();  // Polymorphism: base class pointer, derived class object
    delete obj;  // Proper cleanup using virtual destructor
    return 0;
}
```

**Output:**
```
Base Constructor called
Derived Constructor called
Derived Destructor called
Base Destructor called
```

Without the `virtual` keyword in the base class destructor, only the base class destructor would be called when the object is deleted, which could result in resource leaks if the derived class allocates its own resources.

#### **D. Rule #3: Destructor for Dynamic Memory**
If a constructor allocates memory dynamically (using `new`), the **destructor must free** that memory (using `delete` or `delete[]` for arrays). Failing to do so results in **memory leaks**.

#### **Example of Destructor for Dynamic Memory:**

```cpp
class MyClass {
private:
    int* data;

public:
    MyClass(int val) {
        data = new int(val);  // Allocate memory dynamically
        cout << "Constructor: " << val << endl;
    }

    ~MyClass() {
        delete data;  // Free dynamically allocated memory
        cout << "Destructor called" << endl;
    }
};

int main() {
    MyClass* obj = new MyClass(42);  // Create object dynamically
    delete obj;  // Destructor is automatically called, cleaning up memory
    return 0;
}
```

**Output:**
```
Constructor: 42
Destructor called
```

#### **E. Rule #4: No Parameters in Destructors**
- **Destructors cannot have parameters**, so you cannot overload them. A class can only have one destructor.
  
#### **F. Rule #5: Destructor for Arrays**
If you create an array of objects dynamically using `new[]`, the corresponding destructor should use `delete[]` to delete the array properly.

**Example:**

```cpp
class MyClass {
private:
    int* data;

public:
    MyClass(int val) {
        data = new int(val);
    }

    ~MyClass() {
        delete data;
    }
};

int main() {
    MyClass* arr = new MyClass ;  // Dynamically allocate an array of objects
    delete[] arr;  // Use delete[] to properly destroy the array
    return 0;
}
```

---

### **Summary of Key Rules for Constructors and Destructors:**

1. **Destructor cannot have parameters**: A class can only have one destructor.
2. **Automatic destruction**: The destructor is called automatically when an object goes out of scope or is deleted.
3. **Constructors and destructors must be paired**: If a constructor allocates resources, the destructor must free them.
4. **Destructors are not inherited**: Derived class destructors are not inherited, but base class destructors can be called automatically.
5. **Virtual destructors**: Use a virtual destructor in the base class to ensure proper cleanup when deleting derived class objects through a base class pointer.
6. **Dynamic memory**: Always `delete` dynamically allocated memory to prevent memory leaks.
7. **Use `delete[]` for arrays**: If you allocate an array of objects using `new[]`, use `delete[]` in the destructor to free the memory.

---

Let me know if you'd like to explore any specific examples or clarify anything further!