[C++ Structures (With Examples)](https://www.programiz.com/cpp-programming/structure)

A `struct` in C++ is a user-defined data type where members (variables) are stored in contiguous memory locations, each with its own space. In contrast, a `union` also holds multiple members, but all members share the same memory space, meaning only one member can hold a value at a time. Would you like to delve deeper into a specific use case for either?

---
Unions are best used when you know you'll only need one value at a time, and you want to save memory. Otherwise, if you need to store multiple values simultaneously, use a `struct`.

---


A **`union`** in C++ is a special data type that allows you to store different types of data in the same memory location. The key difference between a union and a struct is that all members of a union **share the same memory**. This means the memory allocated for a union is large enough to hold the largest member of the union, but only one member can hold a value at any given time.

### How Union Manages Memory

1. **Memory Allocation**: The size of a union is determined by the size of its largest member. All members of the union share the same memory, so the total memory required for the union is the size of its largest member, not the sum of the sizes of all the members.

2. **Sharing Memory**: Since all members share the same memory location, the union doesn't allocate separate space for each member like a struct does. Instead, it has a single memory location large enough to store the largest member, and each member's value can overwrite the value of the others.

3. **Memory Layout**: Internally, all members are stored at the same memory address, but you can access each member by referring to its name. However, only the last-written member's value will be valid.

### Example: Union

```cpp
#include <iostream>
using namespace std;

union Data {
    int i;
    float f;
    char c;
};

int main() {
    Data d;

    d.i = 42;          // Set integer
    cout << "d.i: " << d.i << endl;

    d.f = 3.14f;       // Set float (overwrites the integer)
    cout << "d.f: " << d.f << endl;

    d.c = 'A';         // Set char (overwrites the float)
    cout << "d.c: " << d.c << endl;

    // Now, d.i and d.f hold invalid data, as the memory was overwritten by d.c

    return 0;
}
```

### Output:
```
d.i: 42
d.f: 3.14
d.c: A
```

### Key Points About Memory Management in Unions:

1. **Size**: The size of the union is determined by its largest member. For example, if a union has an `int` (4 bytes), a `double` (8 bytes), and a `char` (1 byte), the union will take up 8 bytes (the size of the largest member).

2. **Overwriting Data**: When you assign a value to one member of the union, the memory occupied by other members is overwritten. This is why, when you access a member of a union after writing to another member, you may not get valid data unless you access the most recently written member.

3. **Memory Efficiency**: Unions are memory-efficient when you need to store different types of data but don't need them all at the same time. This is particularly useful in situations like embedded systems or when you're dealing with polymorphism in data structures.

### Example of Union Size Calculation:

```cpp
#include <iostream>
using namespace std;

union Example {
    int i;        // 4 bytes
    double d;     // 8 bytes
    char c;       // 1 byte
};

int main() {
    cout << "Size of union Example: " << sizeof(Example) << " bytes" << endl;
    return 0;
}
```

**Output:**
```
Size of union Example: 8 bytes
```

Here, the union `Example` is 8 bytes in size because the largest member is a `double`, which requires 8 bytes of memory.

### Why Use Unions?

- **Memory Efficiency**: If you need a data structure where only one of several types of data is needed at a time, unions can save memory.
- **Variant Data Types**: Unions are commonly used in situations where a variable can take multiple types of values, such as in certain low-level programming tasks, or when implementing variant types in custom data structures.

### Key Disadvantages:
- **Only One Member at a Time**: Since all members of a union share the same memory, only one member can hold a value at any given time. This can lead to data corruption if you don't manage which member is being used carefully.
- **No Type Safety**: There is no built-in way to track which member of the union is currently valid, which can result in bugs if the wrong member is accessed.

Unions are most useful in cases where you need to work with different types of data but you know you'll only be using one type at any given moment.


---
## ENUM
In C++, an **`enum`** (short for "enumeration") is a user-defined data type that allows you to define a set of named integral constants. It makes the code more readable and maintainable by giving meaningful names to values, which is especially helpful when working with sets of related constants (like days of the week, colors, status codes, etc.).

### Basic Syntax of an Enum:

```cpp
enum EnumName {
    Value1,
    Value2,
    Value3,
    // ...
};
```

By default, the values in an enum are assigned integer values starting from `0`, and each subsequent value gets incremented by 1 unless you specify otherwise.

### Example:

```cpp
#include <iostream>
using namespace std;

enum Color {
    Red,    // Automatically gets the value 0
    Green,  // Automatically gets the value 1
    Blue    // Automatically gets the value 2
};

int main() {
    Color c = Green;

    cout << "Color value: " << c << endl;  // Prints 1 (the value associated with Green)
    
    if (c == Green) {
        cout << "The color is Green!" << endl;
    }

    return 0;
}
```

### Output:
```
Color value: 1
The color is Green!
```

In this case, `Red`, `Green`, and `Blue` are `enum` values, and they are implicitly assigned values starting from `0`. So:
- `Red = 0`
- `Green = 1`
- `Blue = 2`

### Assigning Custom Values to Enum Members:

You can manually assign specific integer values to the members of an `enum`:

```cpp
enum StatusCode {
    OK = 200,        // Assign custom value 200
    NotFound = 404,  // Assign custom value 404
    InternalError = 500  // Assign custom value 500
};

int main() {
    StatusCode code = NotFound;

    if (code == NotFound) {
        cout << "Error 404: Page not found!" << endl;
    }

    return 0;
}
```

### Output:
```
Error 404: Page not found!
```

Here, `StatusCode` has the custom values:
- `OK = 200`
- `NotFound = 404`
- `InternalError = 500`

### Strongly Typed Enums (C++11 and Later):
In C++11 and later, you can define **strongly typed enums** using the `enum class` keyword. This provides better type safety and avoids issues with implicit conversions to integers, which can occur with traditional `enum`s.

#### Example of `enum class`:

```cpp
#include <iostream>
using namespace std;

enum class Direction {
    Up = 1,
    Down = 2,
    Left = 3,
    Right = 4
};

int main() {
    Direction dir = Direction::Up;

    // Cannot implicitly compare an enum class with an integer
    // if (dir == 1) {  // This will give a compile-time error

    if (dir == Direction::Up) {
        cout << "Moving Up!" << endl;
    }

    return 0;
}
```

### Output:
```
Moving Up!
```

#### Key Differences with `enum class`:
1. **Scope**: The values in an `enum class` are scoped to the `enum` itself, which means you must refer to them using the enum name, e.g., `Direction::Up`. In a traditional `enum`, the values are available directly in the global namespace.
   
2. **Type Safety**: With `enum class`, you cannot implicitly convert the enum value to an integer, which makes the code safer and less error-prone. This is especially useful for avoiding accidental misuse, like comparing an `enum` with an integer.

3. **Underlying Type**: In a traditional `enum`, the underlying type is typically an integer (usually `int`), and you can cast it freely. However, in `enum class`, you can explicitly specify the underlying type, and it provides stricter control over the underlying type.

#### Specifying the Underlying Type:
You can also specify the underlying type of an `enum class`, which defaults to `int`. Here's an example where the underlying type is specified as `unsigned char`:

```cpp
enum class Weekday : unsigned char {
    Sunday = 1,
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday
};

int main() {
    Weekday today = Weekday::Monday;
    cout << "Today is Monday!" << endl;

    return 0;
}
```

### Advantages of `enum class`:
- **Scoped**: The values are contained within the enum's scope, preventing accidental name clashes.
- **Type-safe**: Enum class members cannot be implicitly converted to integers, reducing bugs.
- **Custom Underlying Types**: You can specify a custom underlying type for the enum, such as `char`, `short`, or `unsigned int`.

### Summary of Key Points:
1. **Enums** are used to define a set of named constants that represent integral values.
2. **`enum`** (traditional) has implicit integer values starting from `0` and can be assigned specific values.
3. **`enum class`** (introduced in C++11) offers stronger type safety, scoped values, and a choice of underlying type.
4. **Underlying Type**: Both traditional enums and `enum class` can have a specified underlying type (e.g., `int`, `char`), but this must be explicitly stated for `enum class`.

### Practical Use Cases:
- **States or Flags**: Enums are useful for representing states, options, or flags (e.g., menu options, error codes).
- **Improved Readability**: Enums make the code more readable and easier to maintain by replacing magic numbers (e.g., `0`, `1`, `2`) with meaningful names (e.g., `Red`, `Green`, `Blue`).
- **Finite Sets of Values**: Enums are great for representing finite sets of values (e.g., days of the week, months of the year, etc.).

Let me know if you'd like further clarification or examples!