### **Compile-time Polymorphism Overview**

**Compile-time polymorphism** (also known as **static polymorphism**) happens when the decision about which function or operator to invoke is made at compile time, rather than at runtime. In C++, this can be achieved through:

1. **Function Overloading** (which we've covered before)
2. **Operator Overloading** (the focus of this session)

Operator overloading allows you to define how operators (like `+`, `-`, `*`, etc.) behave when applied to user-defined types (e.g., classes). This gives your classes a more natural syntax for interacting with objects.

### **Operator Overloading in C++**

Operator overloading allows you to define the behavior of operators for objects of your own classes. You can define new meanings for operators, such as `+` for adding two complex numbers or `<<` for printing a custom object.

we use operator then + for operator overloading

```cpp
abc operator + (abc& x){

}
```

### **Why Operator Overloading?**

It makes user-defined types behave like built-in types, improving code readability and expressiveness. For example, rather than calling a function to add two `Complex` numbers, you can simply use the `+` operator.

*** Rules for operator overloading ***


---

### **Example 1: Overloading the `+` Operator for Complex Numbers**

Let’s create a simple example with a `Complex` class, and we'll overload the `+` operator to add two complex numbers.

```cpp
#include <iostream>

class abc{
    public:
    int a;
    abc(int x){
        a = x;
    }
    
    abc operator + (abc& x){
        return abc(a + x.a);
    }
};

int main() {
    abc a1(12);
    abc a2(13);
    abc a3 = a1 + a2;
    std::cout << a3.a;

    return 0;
}
```

---

### **Key Points About Operator Overloading:**

1. **Syntax**: To overload an operator, you define a special member function or a non-member function. The operator function has the same name as the operator but as a function.
    
    - For example, `operator+` for `+`, `operator-` for `-`, `operator<<` for `<<`, etc.
2. **Use of `friend` Keyword**: If the operator needs access to private or protected members of the class (like `<<` for printing), we often make the operator function a **friend** of the class.
    
3. **Return Type**: Operator overload functions typically return the result of the operation. For binary operators (like `+`), you return a new object representing the result. For unary operators (like `++`), you might modify the object and return it (either by reference or by value).
    
4. **When to Use**: Operator overloading should be used when it makes the code **more readable** and **intuitive**. Overloading operators for basic operations (like `+`, `-`, `*`, and `<<`) is quite common. But try to avoid overloading operators in ways that could confuse the reader or break expectations.
    

---

### **Summary of Operator Overloading:**

- **Compile-time Polymorphism**: Operator overloading is a form of compile-time polymorphism because the correct operator function is determined at compile time based on the types of the operands.
- You can overload most of the operators in C++ to work with custom types (like classes).
- The goal is to make your custom classes work as naturally as possible with built-in C++ operators, enhancing both **expressiveness** and **readability**.

---

Would you like me to show more examples of operator overloading, or is this enough for now?


---
# using friend fun

Certainly! Let's go over **operator overloading using friend functions** in C++. The **`friend`** keyword allows a non-member function to access the private and protected members of a class. This is particularly useful for operator overloading when you need to access the class's internal data but want the operator to be a non-member function.

### Why Use `friend` Functions for Operator Overloading?

Sometimes, for binary operators (like `+`, `-`, `<<`, etc.), it makes sense to use a **friend function** instead of a member function. This is especially the case when:

- The left operand is not of the class type.
- You want to provide more flexible syntax (e.g., allowing `object + object` or `object + constant`).
- You want the operator to behave more intuitively, especially when it involves interacting with other classes or types.

---

### **Example 1: Overloading the `+` Operator using a Friend Function**

Let’s consider a **`Complex`** class where we want to overload the `+` operator to add two complex numbers. We'll use a **friend function** to allow the operator to access the private members of the class.

```cpp
#include <iostream>

class abc{
    public:
    int a;
    abc(int x){
        a = x;
    }
    
    friend abc operator + (abc& x, abc& y);
};

abc operator + (abc& x, abc& y){
    return abc(y.a + x.a);
}

int main() {
    abc a1(12);
    abc a2(13);
    abc a3 = a1 + a2;
    std::cout << a3.a;

    return 0;
}
```
### **Explanation**:

- **`friend Complex operator + (const Complex& c1, const Complex& c2)`**: We declare the `+` operator as a friend function, allowing it to access the private members (`real` and `imag`) of both `c1` and `c2`.
- The operator function is **defined outside** the class but has access to the class's private members because it is a **friend**.
- We can add two `Complex` objects using the `+` operator just like built-in types, thanks to operator overloading.

---

# dont care
### **Example 2: Overloading the `<<` Operator for Output Using a Friend Function**

Now, let’s overload the `<<` operator to print `Complex` objects using `cout`. We will use a **friend function** for this as well.

```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    double real, imag;
public:
    // Constructor to initialize the complex number
    Complex(double r = 0, double i = 0) : real(r), imag(i) {}

    // Overload the << operator for output using a friend function
    friend ostream& operator << (ostream& os, const Complex& c);

    // Function to display the complex number (not required here, just for reference)
    void display() const {
        cout << real << " + " << imag << "i" << endl;
    }
};

// Define the << operator outside the class, but as a friend function
ostream& operator << (ostream& os, const Complex& c) {
    os << c.real << " + " << c.imag << "i";  // Output complex number in the form "a + bi"
    return os;  // Return the stream to allow chaining
}

int main() {
    Complex c1(3.5, 2.5);

    cout << c1 << endl;  // Output: 3.5 + 2.5i

    return 0;
}
```

### **Explanation**:

- **`friend ostream& operator << (ostream& os, const Complex& c)`**: We overload the `<<` operator as a friend function so that it can access the private members of the `Complex` class.
- The function outputs the `Complex` object in a user-friendly format (`"real + imagi"`).
- We return the output stream (`os`) to allow chaining (i.e., `cout << c1 << c2;`).

---

### **Key Points on Using Friend Functions for Operator Overloading**:

1. **Accessing Private Members**: A friend function can access the private and protected members of the class, which makes it ideal for operators that need to access the internal state of objects.
    
2. **Binary Operators**: Friend functions are often used for binary operators (like `+`, `-`, `*`, `<<`, etc.), especially when one of the operands is not of the class type.
    
3. **Operator Syntax**: The syntax of the operator is typically similar to what we would use with built-in types, which can improve the **readability** of the code. For example, you can write `c1 + c2` instead of calling a method like `c1.add(c2)`.
    
4. **Use Cases for Friend Functions**:
    
    - Overloading stream insertion (`<<`) and extraction (`>>`) operators for printing and reading objects.
    - When the operator involves objects from **different classes**.
    - When you prefer not to change the class interface but still want to allow external functions to interact with private data.

---

### **Summary**:

- **Friend functions** allow us to overload operators while accessing the private members of a class.
- They provide flexibility when overloading binary operators, especially if the operands are of different types.
- In our examples, we used friend functions for both the `+` operator and the `<<` operator to make the syntax more intuitive for users of the `Complex` class.

Would you like to see more examples or dive deeper into any specific topic?
