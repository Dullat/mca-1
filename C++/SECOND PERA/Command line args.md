### Command Line Arguments in C++

Command-line arguments allow a program to accept input from the command line when it is executed, providing flexibility and user control over the program's behavior. In C++, command-line arguments are passed to the `main()` function.

#### Syntax of `main()` with Command-Line Arguments:
```cpp
int main(int argc, char *argv[]) {
    // Code here
}
```

- **`argc` (Argument Count)**: An integer that indicates the number of command-line arguments, including the program name.
- **`argv` (Argument Vector)**: An array of strings (character pointers) representing the command-line arguments. `argv[0]` is the program name, and `argv[1]`, `argv[2]`, ..., are the arguments passed.

#### Example: Basic Command-Line Arguments

```cpp
#include <iostream>
using namespace std;

int main(int argc, char* argv[]) {
    cout << "Number of arguments: " << argc << endl;
    cout << "Program name: " << argv[0] << endl;
    
    // Print all arguments
    for (int i = 1; i < argc; i++) {
        cout << "Argument " << i << ": " << argv[i] << endl;
    }

    return 0;
}
```

#### Example Execution:
```bash
$ ./myprogram hello world 42
```

#### Output:
```
Number of arguments: 4
Program name: ./myprogram
Argument 1: hello
Argument 2: world
Argument 3: 42
```

#### Key Points:
- **`argc`** includes the program name, so the count is always at least 1.
- **`argv[0]`** is the program name, and `argv[1]`, `argv[2]`, ... are the arguments.
- Command-line arguments are **strings**. To use them as other types (e.g., integers), you may need to **convert** them using functions like `stoi()` or `atoi()`.

#### Example: Using Command-Line Arguments as Integers

```cpp
#include <iostream>
#include <cstdlib>  // For atoi() function
using namespace std;

int main(int argc, char* argv[]) {
    if (argc != 3) {
        cout << "Usage: <program> <num1> <num2>" << endl;
        return 1;
    }

    int num1 = atoi(argv[1]);  // Convert argument to integer
    int num2 = atoi(argv[2]);

    cout << "Sum: " << num1 + num2 << endl;
    return 0;
}
```

#### Example Execution:
```bash
$ ./myprogram 10 20
```

#### Output:
```
Sum: 30
```

### Summary:
- **`argc`**: Counts the number of arguments.
- **`argv`**: Array of strings representing the arguments.
- Command-line arguments provide a way to pass input values to the program when it's executed.
