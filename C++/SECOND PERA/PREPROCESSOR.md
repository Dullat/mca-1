### Preprocessor Directives in C++
[C Preprocessors - GeeksforGeeks](https://www.geeksforgeeks.org/cc-preprocessors/)

Preprocessor directives are commands that are processed before the actual compilation of a C++ program. They are used to perform operations like file inclusion, macro definitions, conditional compilation, etc. These directives are not part of the C++ language itself, but they are handled by the preprocessor before the code is compiled.

#### Common Preprocessor Directives:

1. **`#include`**: Includes a file (typically header files) in your program.
   - **Syntax**:
     ```cpp
     #include <header_file>    // Standard library file (e.g., <iostream>)
     #include "file_name"      // User-defined file (e.g., "myfile.h")
     ```
   - **Example**:
     ```cpp
     #include <iostream>  // Includes the standard iostream library
     ```

2. **`#define`**: Defines a macro or constant.
   - **Syntax**:
     ```cpp
     #define MACRO_NAME value
     ```
   - **Example**:
     ```cpp
     #define PI 3.14
     ```
     This replaces `PI` with `3.14` wherever it appears in the code.

3. **`#undef`**: Undefines a previously defined macro.
   - **Syntax**:
     ```cpp
     #undef MACRO_NAME
     ```

4. **`#if`, `#else`, `#elif`, `#endif`**: Conditional compilation.
   - Used to include or exclude parts of the code based on conditions.
   - **Example**:
     ```cpp
     #define DEBUG
     #if defined(DEBUG)
         cout << "Debugging is enabled." << endl;
     #else
         cout << "Debugging is disabled." << endl;
     #endif
     ```

5. **`#ifdef` / `#ifndef`**: Checks if a macro is defined (or not).
   - **Syntax**:
     ```cpp
     #ifdef MACRO_NAME
     #ifndef MACRO_NAME
     ```
   - **Example**:
     ```cpp
     #ifdef DEBUG
         cout << "Debugging enabled." << endl;
     #endif
     ```

6. **`#pragma`**: Provides special instructions to the compiler. (Compiler-specific)
   - **Example**:
     ```cpp
     #pragma once  // Ensures a header file is included only once.
     ```

7. **`#error`**: Generates a compile-time error with a custom message.
   - **Syntax**:
     ```cpp
     #error "Error message"
     ```

8. **`#line`**: Changes the current line number in error messages.
   - **Syntax**:
     ```cpp
     #line number "file_name"
     ```

---

### Example Using Preprocessor Directives:

```cpp
#include <iostream>
#define PI 3.14

int main() {
    std::cout << "Value of PI: " << PI << std::endl;

    #ifdef DEBUG
    std::cout << "Debugging enabled" << std::endl;
    #endif
    
    return 0;
}
```

---

### Summary:

- **`#include`**: Includes files.
- **`#define`**: Defines constants or macros.
- **`#if` / `#ifdef`**: Conditional compilation.
- **`#pragma`**: Compiler-specific instructions.
- **`#error`**: Generates errors during compilation.

Preprocessor directives provide powerful tools for controlling compilation and improving code portability and flexibility.