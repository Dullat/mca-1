
## Identifier
identifiers are names used to identify variables, functions, arrays, and other user-defined items.

#### Rules for Identifiers

1. **Start with a Letter or Underscore**: Identifiers must begin with a letter (either uppercase or lowercase) or an underscore (`_`). They cannot start with a digit.
   ``` 
   int myVariable;   // Valid
   int _myVariable;  // Valid
   int 2myVariable;  // invalid
   ```


1. **Followed by Letters, Digits, or Underscores**: After the first character, identifiers can contain letters, digits, and underscores.
   ```
   int myVariable1; // Valid
   int my_Variable; // Valid
   int myVariable!; // Invalid (exclamation mark is not allowed)
   ```
   

1. **Case Sensitivity**: Identifiers in C++ are case-sensitive, meaning `myVariable`, `MyVariable`, and `MYVARIABLE` would be considered different identifiers.
   
4. **No Reserved Keywords**: Identifiers cannot be the same as C++ reserved keywords (e.g., `int`, `if`, `return`).
   
   ```
   int int; // invalid
   int for; // invalid
   ```
6. **Length**: There is no standard limit on the length of an identifier, but it’s best to use meaningful and reasonably short names. Some compilers may have practical limits.
`int aVeryLongIdentifierNameThatShouldBeAvoidedForReadability;`

---
## keywords

keywords are reserved words that have special meaning to the compiler. You cannot use these keywords as identifiers (names for variables, functions, or other entities) in your code. Keywords define the syntax and structure of the C++ language.

such as **void**, **int**, **public**, etc. It can’t be used for a variable name or function name or any other identifiers. The total count of reserved keywords is 95

|          |                                                                                     |           |                                                              |
| -------- | ----------------------------------------------------------------------------------- | --------- | ------------------------------------------------------------ |
| asm      | double                                                                              | new       | [switch](https://www.geeksforgeeks.org/switch-statement-cc/) |
| auto     | else                                                                                | operator  | template                                                     |
| break    | enum                                                                                | private   | this                                                         |
| case     | extern                                                                              | protected | throw                                                        |
| catch    | float                                                                               | public    | try                                                          |
| char     | for                                                                                 | register  | typedef                                                      |
| class    | friend                                                                              | return    | union                                                        |
| const    | goto                                                                                | short     | unsigned                                                     |
| continue | [if](https://www.geeksforgeeks.org/check-if-given-number-is-perfect-square-in-cpp/) | signed    | virtual                                                      |
| default  | inline                                                                              | sizeof    | void                                                         |
| delete   | int                                                                                 | static    | volatile                                                     |
| do       | long                                                                                | struct    | while                                                        |

---
## Constants
Constants in C++ refer to variables with fixed values that cannot be changed. Once they are defined in the program, they remain constant throughout the execution of the program. They are generally stored as read-only tokens in the code segment of the memory of the program. They can be of any available data type in C++ such as int, char, string, etc.

#### How to Define Constants in C++?

We can define the constants in C++ using three ways:

1. **Using const Keyword**
2. **Using constexpr Keyword**
3. **Using #define Preprocessor**

`const DATATYPE _variable_name_ = value;`

---

## Data types in c++

All [variables](https://www.geeksforgeeks.org/variables-and-keywords-in-c/) use data type during declaration to restrict the type of data to be stored. Therefore, we can say that data types are used to tell the variables the type of data they can store

C++ provides a wide range of data types, including:


![[Pasted image 20240901102100.png]]

### Primitive:
These data types are built-in or predefined data types and can be used directly by the user to declare variables. example: int, char, float, bool, etc.

1. **Integer types**:
    - `int`: 4-byte, range: -2147483648 to 2147483647
    - `short`: 2-byte, range: -32768 to 32767
    - `long`: 4-byte, range: -2147483648 to 2147483647
    - `long long`: 8-byte, range: -9223372036854775808 to 9223372036854775807
2. **Floating-point types**:
    - `float`: 4-byte, precision: 6 decimal digits
    - `double`: 8-byte, precision: 15 decimal digits
    - `long double`: 12-byte, precision: 30 decimal digits
3. **Character types**:
    - `char`: 1-byte, represents a single character
    - `wchar_t`: 2-byte or 4-byte, represents a wide character
    - `char16_t` and `char32_t`: 2-byte and 4-byte, respectively, represent Unicode characters
4. **Boolean type**:
    - `bool`: 1-byte, represents true or false
5. **String type**:
    - `std::string`: a class that represents a sequence of characters

### Derived Data Types:
 [Derived data types](https://www.geeksforgeeks.org/derived-data-types-in-c/) that are derived from the primitive or built-in datatypes are referred to as Derived Data Types

1. **Pointers**
    
    - Store memory addresses of other variables.
2. **Arrays**
    
    - Collection of elements of the same type.
3. **Functions**
    
    - Used to define a block of code that performs a specific task and can return a value.
4. **References**
    
    - An alias for another variable. Must be initialized when declared.

### User-Defined Data Types:
 [Abstract or User-Defined data types](https://www.geeksforgeeks.org/user-defined-derived-data-types-in-c/) are defined by the user itself. Like, defining a class in C++ or a structure. C++ provides the following user-defined datatypes:

1. **Structures (`struct`)**
    
    - Used to group different data types into a single unit.
2. **Unions (`union`)**
    
    - Similar to structures but all members share the same memory location.
3. **Enumerations (`enum`)**
    
    - Define a set of named integer constants.
4. **Classes**
    
    - Used in object-oriented programming to define objects that bundle data and functions.

---
## Operarators
In C++, operators are symbols that perform operations on variables and values. Here's an overview of the different types of operators available in C++:
![[Pasted image 20241114194657.png]]

#### 1. Arithmetic Operators

These operators perform basic arithmetic operations:

- `+` (Addition): Adds two operands. Example: `a + b`
- `-` (Subtraction): Subtracts the second operand from the first. Example: `a - b`
- `*` (Multiplication): Multiplies two operands. Example: `a * b`
- `/` (Division): Divides the first operand by the second. Example: `a / b`
- `%` (Modulus): Returns the remainder of division. Example: `a % b`

#### 2. Relational Operators

These operators compare two values and return a boolean result:

- `==` (Equal to): Checks if two operands are equal. Example: `a == b`
- `!=` (Not equal to): Checks if two operands are not equal. Example: `a != b`
- `>` (Greater than): Checks if the first operand is greater than the second. Example: `a > b`
- `<` (Less than): Checks if the first operand is less than the second. Example: `a < b`
- `>=` (Greater than or equal to): Checks if the first operand is greater than or equal to the second. Example: `a >= b`
- `<=` (Less than or equal to): Checks if the first operand is less than or equal to the second. Example: `a <= b`

#### 3. Logical Operators

These operators are used to combine or invert boolean values:

- `&&` (Logical AND): Returns true if both operands are true. Example: `a && b`
- `||` (Logical OR): Returns true if at least one of the operands is true. Example: `a || b`
- `!` (Logical NOT): Inverts the boolean value of the operand. Example: `!a`

#### 4. Bitwise Operators

These operate on the binary representations of integers:

- `&` (Bitwise AND): Performs a bitwise AND operation. Example: `a & b`
- `|` (Bitwise OR): Performs a bitwise OR operation. Example: `a | b`
- `^` (Bitwise XOR): Performs a bitwise XOR operation. Example: `a ^ b`
- `~` (Bitwise NOT): Inverts all bits of the operand. Example: `~a`
- `<<` (Left shift): Shifts bits to the left, filling with zeros. Example: `a << 2`
- `>>` (Right shift): Shifts bits to the right, sign-extending or filling with zeros. Example: `a >> 2`

#### 5. Assignment Operators

These operators assign values to variables:

- `=` (Assignment): Assigns the right operand's value to the left operand. Example: `a = b`
- `+=` (Addition assignment): Adds the right operand to the left operand and assigns the result to the left operand. Example: `a += b` (equivalent to `a = a + b`)
- `-=` (Subtraction assignment): Subtracts the right operand from the left operand and assigns the result to the left operand. Example: `a -= b` (equivalent to `a = a - b`)
- `*=` (Multiplication assignment): Multiplies the left operand by the right operand and assigns the result to the left operand. Example: `a *= b` (equivalent to `a = a * b`)
- `/=` (Division assignment): Divides the left operand by the right operand and assigns the result to the left operand. Example: `a /= b` (equivalent to `a = a / b`)
- `%=` (Modulus assignment): Applies the modulus operator and assigns the result to the left operand. Example: `a %= b` (equivalent to `a = a % b`)

#### 6. Increment and Decrement Operators

These operators increase or decrease a variable's value by one:

- `++` (Increment): Increases the value of the operand by one. Can be prefix (`++a`) or postfix (`a++`).
- `--` (Decrement): Decreases the value of the operand by one. Can be prefix (`--a`) or postfix (`a--`).

#### 7. Conditional (Ternary) Operator**

A shorthand for an `if-else` statement:

- `? :` (Ternary): Evaluates a condition and returns one of two values. Example: `condition ? expr1 : expr2`

#### 8. Comma Operator

- `,` (Comma): Evaluates two expressions and returns the result of the second. Example: `a = (b = 2, b + 1);` (first `b` is assigned 2, then `b + 1` is evaluated)

#### 9. Member Access Operators

- `.` (Member access): Accesses a member of an object. Example: `object.member`
- `->` (Pointer to member access): Accesses a member of an object through a pointer. Example: `pointer->member`

#### 10. Scope Resolution Operator

- `::` (Scope resolution): Accesses global variables or methods and static members of a class. Example: `std::cout`

#### 11. Type Casting Operators

- `static_cast<T>`: Performs a static type conversion. Example: `static_cast<int>(3.14)`
- `dynamic_cast<T>`: Performs a safe downcast. Example: `dynamic_cast<Derived*>(basePtr)`
- `const_cast<T>`: Adds or removes `const` qualification. Example: `const_cast<int&>(constVar)`
- `reinterpret_cast<T>`: Performs low-level type casting. Example: `reinterpret_cast<int*>(ptr)`

---
## Size of operator

The `sizeof` operator in C++ is used to determine the size, in bytes, of a data type or object. It is a compile-time operator that provides the size of a variable or type, which is useful for understanding memory usage and managing buffers.

#### Syntax
```
sizeof(expression)
sizeof(type)
```

#### Examples
#### 1. Size of a Data Type

To get the size of built-in data types:
```
#include <iostream>

int main() {
    std::cout << "Size of int: " << sizeof(int) << " bytes\n";
    std::cout << "Size of float: " << sizeof(float) << " bytes\n";
    std::cout << "Size of double: " << sizeof(double) << " bytes\n";
    std::cout << "Size of char: " << sizeof(char) << " bytes\n";
    return 0;
}
```

#### 2. Size of array

```
#include <iostream>

int main() {
    int arr[10];
    std::cout << "Size of array: " << sizeof(arr) << " bytes\n";
    std::cout << "Number of elements in array: " << sizeof(arr) / sizeof(arr[0]) << '\n';
    return 0;
}
```

#### 3. Size of var
```
#include <iostream>

int main() {
    int a;
    double b;
    std::cout << "Size of variable a: " << sizeof(a) << " bytes\n";
    std::cout << "Size of variable b: " << sizeof(b) << " bytes\n";
    return 0;
}

```

#### 4. Size of class or structure
```
#include <iostream>

struct Example {
    int a;
    char b;
    double c;
};

int main() {
    std::cout << "Size of Example struct: " << sizeof(Example) << " bytes\n";
    return 0;
}
```

#### 5. Size of pointer
```
int size = sizeof(ptr)
```

### Note:
- `sizeof` is evaluated at compile-time, so it does not incur runtime overhead.
- For dynamically allocated arrays (e.g., allocated with `new`), `sizeof` cannot be used to determine the size of the allocated memory. You must keep track of this size manually.

---

## Operator Precedence

Operator precedence determines which operators are evaluated first in an expression. Operators with higher precedence are evaluated before operators with lower precedence.

### Operator Associativity

Operator associativity defines the order in which operators of the same precedence level are evaluated. Associativity can be left-to-right or right-to-left.

#### Precedence and Associativity Table

Here is a summary of C++ operators organized by precedence, from highest to lowest, along with their associativity:

| Precedence | Operators                                                                                                                                                                                                                                                                                            | Associativity              |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| 1          | `::` (Scope resolution), `.` (Member access), `->` (Pointer to member access)                                                                                                                                                                                                                        | Left-to-right              |
| 2          | `++` (Increment), `--` (Decrement), `+` (Unary plus), `-` (Unary minus), `!` (Logical NOT), `~` (Bitwise NOT), `*` (Dereference), `&` (Address-of)                                                                                                                                                   | Right-to-left              |
| 3          | `*` (Multiplication), `/` (Division), `%` (Modulus)                                                                                                                                                                                                                                                  | Left-to-right              |
| 4          | `+` (Addition), `-` (Subtraction)                                                                                                                                                                                                                                                                    | Left-to-right              |
| 5          | `<<` (Left shift), `>>` (Right shift)                                                                                                                                                                                                                                                                | Left-to-right              |
| 6          | `<` (Less than), `<=` (Less than or equal to), `>` (Greater than), `>=` (Greater than or equal to)                                                                                                                                                                                                   | Left-to-right              |
| 7          | `==` (Equal to), `!=` (Not equal to)                                                                                                                                                                                                                                                                 | Left-to-right              |
| 8          | `&` (Bitwise AND)                                                                                                                                                                                                                                                                                    | Left-to-right              |
| 9          | `^` (Bitwise XOR)                                                                                                                                                                                                                                                                                    | Left-to-right              |
| 10         | `                                                                                                                                                                                                                                                                                                    | ` (Bitwise OR)             |
| 11         | `&&` (Logical AND)                                                                                                                                                                                                                                                                                   | Left-to-right              |
| 12         | `                                                                                                                                                                                                                                                                                                    |                            |
| 13         | `? :` (Conditional)                                                                                                                                                                                                                                                                                  | Right-to-left              |
| 14         | `=` (Assignment), `+=` (Addition assignment), `-=` (Subtraction assignment), `*=` (Multiplication assignment), `/=` (Division assignment), `%=` (Modulus assignment), `<<=` (Left shift assignment), `>>=` (Right shift assignment), `&=` (Bitwise AND assignment), `^=` (Bitwise XOR assignment), ` | =` (Bitwise OR assignment) |
| 15         | `,` (Comma)                                                                                                                                                                                                                                                                                          | Left-to-right              |
| 16         | `::` (Scope resolution)                                                                                                                                                                                                                                                                              | N/A                        |
| 17         | `[]` (Array subscript), `()` (Function call), `.` (Member access), `->` (Pointer to member access)                                                                                                                                                                                                   | Left-to-right              |

---
In C++, **modifiers** are keywords that modify the properties of variables, data types, and functions. They change the default behavior or properties of types, such as whether a variable can be modified, whether it is shared across threads, or whether it is constant. There are different categories of modifiers in C++ that apply to variables, functions, and even types.

### Types of Modifiers in C++:

1. **Type Modifiers** (e.g., `signed`, `unsigned`, `short`, `long`)
2. **Storage Class Modifiers** (e.g., `static`, `extern`, `mutable`, `register`)
3. **Const Qualifiers** (e.g., `const`)
4. **Function Modifiers** (e.g., `inline`, `virtual`, `explicit`)

---

### 1. Type Modifiers

Type modifiers in C++ are used to alter the size or the behavior of a data type. The most commonly used type modifiers are:

- **`signed`**: Specifies that the integer type can represent both negative and positive values. By default, integer types like `int` are signed.
- **`unsigned`**: Specifies that the integer type can only represent non-negative values (i.e., positive values and zero).
- **`short`**: Specifies that the integer type is of smaller size (typically 16 bits).
- **`long`**: Specifies that the integer type is of larger size (typically 64 bits on some systems).
- **`long long`**: A larger integer type than `long`, typically 64 bits on all platforms.

#### Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    signed int a = -10;      // a can be negative or positive
    unsigned int b = 10;     // b can only be positive
    short int c = 32767;     // Typically 16 bits
    long long int d = 9223372036854775807; // 64 bits

    cout << "signed int: " << a << endl;
    cout << "unsigned int: " << b << endl;
    cout << "short int: " << c << endl;
    cout << "long long int: " << d << endl;

    return 0;
}
```

### 2. Storage Class Modifiers

[Storage Classes in C++ with Examples - GeeksforGeeks](https://www.geeksforgeeks.org/storage-classes-in-c-with-examples/)

Storage class modifiers define the lifetime, visibility, and memory location of variables or functions. Here are the common ones:

- **`static`**: 
  - For variables: It limits the variable's scope to the block or function in which it is declared, but keeps its value between function calls. A `static` variable retains its value throughout the program's lifetime.
  - For functions: A function declared as `static` in a file is only visible in that file (internal linkage).
  
- **`extern`**: Indicates that a variable or function is defined elsewhere, typically in another file. It allows access to global variables/functions across multiple files.

- **`mutable`**: Used in a class to allow a member variable to be modified even if the object itself is declared as `const`.

- **`register`**: A suggestion to the compiler to store the variable in a CPU register (instead of RAM) for faster access. However, modern compilers ignore this.

#### Example:

```cpp
#include <iostream>
using namespace std;

static int counter = 0; // Retains its value between function calls

void increment() {
    static int num = 0; // Static variable: retains its value
    num++;
    counter++;
    cout << "num: " << num << ", counter: " << counter << endl;
}

int main() {
    increment();
    increment();
    increment();

    return 0;
}
```

### 3. `const` Qualifier

The **`const`** keyword is used to declare variables or pointers whose values cannot be modified after initialization. It can be used with both variables and pointers.

- **Const variables**: Variables that cannot be changed after initialization.
- **Const pointers**: You can have const pointers (pointer's value can't be changed) or pointer-to-const (the value being pointed to can't be changed).
- **Const member functions**: Member functions that promise not to modify the state of the object.

#### Example:

```cpp
#include <iostream>
using namespace std;

int main() {
    const int x = 10;   // x cannot be modified
    // x = 20;  // Error: assignment of read-only variable 'x'

    int a = 10;
    const int* ptr = &a;   // Pointer to const: the value pointed to cannot be modified
    // *ptr = 20;  // Error: modification of read-only location

    int* const ptr2 = &a;  // Const pointer: the pointer itself cannot be changed
    ptr2 = &a;  // Error: 'ptr2' is a const pointer and cannot point to another address

    return 0;
}
```

### 4. Function Modifiers

Certain modifiers are used with functions to change their behavior.

- **`inline`**: This suggests to the compiler to replace the function call with the actual code of the function. This can speed up execution for small functions but may increase code size.
  
- **`virtual`**: Used in the context of polymorphism. A `virtual` function can be overridden in derived classes. It allows dynamic dispatch (runtime binding) for function calls.
  
- **`explicit`**: Used in constructor declarations to prevent implicit conversions and copy-initialization.

#### Example:

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    virtual void display() {  // Virtual function
        cout << "Base class display" << endl;
    }
};

class Derived : public Base {
public:
    void display() override {  // Override base class method
        cout << "Derived class display" << endl;
    }
};

void foo(int x) {
    cout << "Value: " << x << endl;
}

inline int square(int x) {  // Inline function
    return x * x;
}

int main() {
    Base* basePtr;
    Derived derivedObj;
    basePtr = &derivedObj;

    basePtr->display();  // Calls Derived class version because of virtual function

    int result = square(5); // Inline function will replace the call with its definition
    cout << "Square of 5: " << result << endl;

    return 0;
}
```

### 5. Other Modifiers

- **`volatile`**: Indicates that a variable may be changed by something outside the control of the program, such as hardware or another thread. This modifier prevents the compiler from optimizing the variable.
  
- **`noexcept`**: Specifies that a function will not throw any exceptions.

#### Example:

```cpp
#include <iostream>
using namespace std;

void foo() noexcept {  // This function guarantees not to throw exceptions
    cout << "This function won't throw exceptions!" << endl;
}

int main() {
    foo();
    return 0;
}
```

### Summary of C++ Modifiers:

| Modifier        | Description                                         |
|-----------------|-----------------------------------------------------|
| `signed`        | Specifies that the integer type can hold negative values. |
| `unsigned`      | Specifies that the integer type can only hold positive values. |
| `short`         | Specifies a smaller integer size. |
| `long`          | Specifies a larger integer size. |
| `static`        | Limits the scope of a variable to the file or function. |
| `extern`        | Declares a variable or function that is defined elsewhere (typically in another file). |
| `mutable`       | Allows a class member to be modified even if the object is `const`. |
| `register`      | Suggests storing a variable in a CPU register for faster access. |
| `const`         | Indicates that the value of a variable cannot be modified. |
| `inline`        | Suggests to the compiler to replace the function call with the function code. |
| `virtual`       | Enables runtime polymorphism (virtual function calls). |
| `explicit`      | Prevents implicit conversions and copy-initialization. |
| `volatile`      | Indicates that a variable can be modified outside the program’s control (e.g., by hardware). |
| `noexcept`      | Specifies that a function will not throw any exceptions. |

Modifiers allow you to fine-tune the behavior of your variables and functions, providing control over memory usage, performance, and safety. Let me know if you'd like to dive deeper into any specific modifier!

---
### Refrence variables
[References in C++ - GeeksforGeeks](https://www.geeksforgeeks.org/references-in-cpp/)