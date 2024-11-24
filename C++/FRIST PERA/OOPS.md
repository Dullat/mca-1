Great that you're preparing for your C++ exam! Let's go over the concept of **Object-Oriented Programming (OOP)** and its key characteristics.
https://www.geeksforgeeks.org/object-oriented-programming-in-cpp/

### What is Object-Oriented Programming (OOP)?

Object-Oriented Programming (OOP) is a programming paradigm that is centered around **objects** rather than actions and logic. It is based on the concept of **objects**, which are instances of **classes**. In OOP, we model real-world entities as objects and define their behaviors (methods) and properties (attributes). The goal is to make software more modular, reusable, and easier to maintain.

### Key Characteristics of OOP

OOP is defined by the following four main principles:

1. **Encapsulation**
   - **Encapsulation** is the bundling of data (variables) and methods (functions) that operate on the data into a single unit called a **class**. 
   - It restricts direct access to some of the object's components and can prevent the accidental modification of data.
   - It is implemented by making class variables private (or protected) and providing public methods (getter and setter) to access and modify the data.

   **Example**:
   ```cpp
   class Person {
   private:
       string name;
       int age;
   public:
       // Getter
       string getName() {
           return name;
       }
       // Setter
       void setName(string n) {
           name = n;
       }
   };
   ```

2. **Abstraction**
   - **Abstraction** is the concept of hiding the complex implementation details and showing only the essential features of an object.
   - It allows the programmer to focus on what an object does, rather than how it does it.
   - In C++, this is often implemented using abstract classes and interfaces.

   **Example**:
   ```cpp
   class Shape {
   public:
       virtual void draw() = 0;  // Pure virtual function (abstract)
   };
   class Circle : public Shape {
   public:
       void draw() override {
           cout << "Drawing a circle" << endl;
       }
   };
   ```

3. **Inheritance**
   - **Inheritance** allows one class (called the **derived class**) to inherit the properties and behaviors (attributes and methods) from another class (called the **base class**).
   - This promotes code reuse, and allows new classes to be built upon existing ones.

   **Example**:
   ```cpp
   class Animal {
   public:
       void speak() {
           cout << "Animal speaks" << endl;
       }
   };
   
   class Dog : public Animal {
   public:
       void speak() {
           cout << "Dog barks" << endl;
       }
   };
   ```

4. **Polymorphism**
   - **Polymorphism** means "many forms," and it allows objects of different classes to be treated as objects of a common base class.
   - It enables a single interface to be used for different data types. There are two main types of polymorphism:
     - **Compile-time polymorphism (Method Overloading and Operator Overloading)**: It is resolved during compilation.
     - **Runtime polymorphism (Method Overriding)**: It is resolved during runtime through dynamic dispatch.

   **Example** (Runtime Polymorphism):
   ```cpp
   class Animal {
   public:
       virtual void sound() {
           cout << "Some animal sound" << endl;
       }
   };
   
   class Dog : public Animal {
   public:
       void sound() override {
           cout << "Woof Woof" << endl;
       }
   };
   
   class Cat : public Animal {
   public:
       void sound() override {
           cout << "Meow" << endl;
       }
   };

   void makeSound(Animal* animal) {
       animal->sound();
   }

   int main() {
       Dog dog;
       Cat cat;

       makeSound(&dog); // Woof Woof
       makeSound(&cat); // Meow
   }
   ```

### Summary of the Four Main OOP Principles:
1. **Encapsulation**: Protects object data and ensures it is accessed only through specific methods.
2. **Abstraction**: Hides implementation details and shows only necessary parts of the object.
3. **Inheritance**: Reuses code and creates hierarchical relationships between classes.
4. **Polymorphism**: Allows different classes to be treated as instances of a common base class, enabling flexibility in code behavior.

---

These concepts are fundamental to OOP, and mastering them will help you understand how C++ (and many other languages) enable object-oriented design. Let me know if you'd like further explanation or examples!