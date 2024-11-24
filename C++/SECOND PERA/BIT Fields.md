[C++ | Bit fields](https://devtut.github.io/cpp/bit-fields.html#declaration-and-usage)

In C++, **bit fields** allow you to allocate a specific number of bits for each member variable within a structure. This is useful when you need to manage memory more efficiently, especially when you're working with hardware or network protocols, where data is often packed into a compact bit-level representation.

### 1. **What Are Bit Fields?**

A **bit field** is a special type of structure member that is allocated a specified number of bits (instead of the usual number of bytes). Bit fields are most commonly used when you need to control the size of the data, which is often required in systems programming or when interfacing with hardware.

#### Syntax for Bit Fields:

```cpp
struct StructureName {
    type member_name : number_of_bits;
};
```

- **`type`**: The data type of the bit field (e.g., `int`, `unsigned int`, etc.).
- **`member_name`**: The name of the bit field member.
- **`: number_of_bits`**: The number of bits allocated to this field. It must be a positive integer.

#### Example:

```cpp
#include <iostream>
using namespace std;

struct Flags {
    unsigned int a : 3;  // 3 bits for 'a'
    unsigned int b : 5;  // 5 bits for 'b'
    unsigned int c : 4;  // 4 bits for 'c'
};

int main() {
    Flags flags;

    flags.a = 5;  // Can hold values between 0 and 7 (3 bits)
    flags.b = 18; // Can hold values between 0 and 31 (5 bits)
    flags.c = 12; // Can hold values between 0 and 15 (4 bits)

    cout << "a: " << flags.a << endl;
    cout << "b: " << flags.b << endl;
    cout << "c: " << flags.c << endl;

    return 0;
}
```

### Output:
```
a: 5
b: 18
c: 12
```

### 2. **Key Characteristics of Bit Fields:**

1. **Memory Efficiency**:
   Bit fields allow you to store data in a very compact manner. Instead of using a full integer (typically 4 bytes or 32 bits), you can use only the number of bits you need. This is especially useful when working with large arrays or structures that need to store many small flags or values.

2. **Alignment and Padding**:
   The C++ standard does not guarantee that bit fields will be packed tightly together. The compiler might insert padding to maintain alignment constraints. For example, a `3-bit` field might take up 4 bytes because of alignment restrictions, depending on the compiler and platform.

3. **Signed vs. Unsigned**:
   Bit fields can be signed or unsigned, but it's important to note that when a signed bit field is used, the leftmost bit (the highest bit) is treated as the sign bit (similar to how negative numbers are represented in two's complement).

4. **Limitations**:
   - **Bit fields must be part of a structure**: They cannot exist outside of a structure.
   - **Bit fields cannot be accessed using pointers**: This is because the actual memory layout and size of the bit fields are dependent on the implementation and the alignment restrictions of the compiler.
   - **Size Limit**: The number of bits allocated cannot exceed the width of the underlying type (for example, you can’t have a 33-bit field if the underlying type is `int` which typically has 32 bits on most platforms).

### 3. **Practical Example: Using Bit Fields for Flags**

Suppose you're designing a system that needs to store multiple flags (e.g., on/off switches) in a compact format. Using bit fields is a great way to save memory.

#### Example: Flags for User Permissions

```cpp
#include <iostream>
using namespace std;

struct UserPermissions {
    unsigned int read : 1;  // 1 bit for read permission
    unsigned int write : 1; // 1 bit for write permission
    unsigned int execute : 1; // 1 bit for execute permission
    unsigned int admin : 1; // 1 bit for admin permission
    unsigned int reserved : 4; // 4 bits for padding or reserved bits
};

int main() {
    UserPermissions permissions;

    // Assigning values to the permissions
    permissions.read = 1;      // Read permission granted
    permissions.write = 0;     // Write permission denied
    permissions.execute = 1;   // Execute permission granted
    permissions.admin = 0;     // Admin permission denied

    cout << "Read: " << permissions.read << endl;
    cout << "Write: " << permissions.write << endl;
    cout << "Execute: " << permissions.execute << endl;
    cout << "Admin: " << permissions.admin << endl;

    return 0;
}
```

### Output:
```
Read: 1
Write: 0
Execute: 1
Admin: 0
```

#### Explanation:
- In the `UserPermissions` structure, each permission is stored as a single bit (`1` or `0`).
- **`read`, `write`, `execute`, and `admin`** each use 1 bit, and there are 4 additional reserved bits.
- This structure only uses **8 bits** (1 byte), instead of using a larger data type like `int` (typically 32 bits), which would be wasteful if you only need a few flags.

### 4. **Bit Fields with Larger Data Types**

Bit fields don’t have to be just `1` bit wide. You can specify how many bits you want for a field, and it can be any integer number (e.g., 3, 8, 12, etc.), depending on the underlying type.

#### Example: Storing Small Numbers in a Struct

```cpp
#include <iostream>
using namespace std;

struct Color {
    unsigned int red : 5;   // 5 bits for red (0-31)
    unsigned int green : 6; // 6 bits for green (0-63)
    unsigned int blue : 5;  // 5 bits for blue (0-31)
};

int main() {
    Color color;

    color.red = 15;   // 5 bits, value between 0-31
    color.green = 45; // 6 bits, value between 0-63
    color.blue = 20;  // 5 bits, value between 0-31

    cout << "Red: " << color.red << endl;
    cout << "Green: " << color.green << endl;
    cout << "Blue: " << color.blue << endl;

    return 0;
}
```

### Output:
```
Red: 15
Green: 45
Blue: 20
```

#### Explanation:
- **`red`** is allocated 5 bits, allowing values between 0 and 31.
- **`green`** is allocated 6 bits, allowing values between 0 and 63.
- **`blue`** is allocated 5 bits, allowing values between 0 and 31.
- This approach uses only **16 bits** (2 bytes) instead of using a full `int`, which would typically require 32 bits.

### 5. **Bit Field Alignment and Padding**

Compilers may add padding between bit fields to ensure proper alignment. The alignment rules can vary depending on the platform, but the general rule is that data types are typically aligned to their natural boundary (e.g., 4-byte alignment for `int`).

#### Example of Padding:

```cpp
#include <iostream>
using namespace std;

struct Sample {
    unsigned int a : 5;  // 5 bits
    unsigned int b : 3;  // 3 bits
    unsigned int c : 10; // 10 bits
};

int main() {
    Sample sample;

    cout << "Size of Sample struct: " << sizeof(sample) << " bytes" << endl;

    return 0;
}
```

### Output:
```
Size of Sample struct: 8 bytes
```

- Even though the `Sample` structure only needs **18 bits** (5 + 3 + 10), it occupies **8 bytes** because of the padding added by the compiler to satisfy the alignment constraints.

### 6. **Bit Fields and Signed Types**

You can also use **signed types** for bit fields. When you use signed types like `int` or `short` for bit fields, the leftmost bit is treated as the **sign bit** (in two's complement representation).

#### Example: Signed Bit Field:

```cpp
#include <iostream>
using namespace std;

struct SignedBitField {
    int a : 3;  // Signed 3-bit field
};

int main() {
    SignedBitField sbf;

    sbf.a = -4;  // Can store values between -4 and 3 (3-bit signed)
    cout << "Value of a: " << sbf.a << endl;

    return 0;
}
```

### Output:
```
Value of a: -4
```

- **`a`** is a signed 3-bit field, which can hold values between -4 and 3 in two's complement representation.

---

### Summary:

- **Bit fields** allow you to allocate a specified number of bits for each member variable within a structure.
- They are useful for memory-efficient storage when dealing with flags, small integers, or hardware interfaces.
- Bit fields can be **signed or unsigned**, and you can specify any number of bits (within the limits of the underlying type).
- The