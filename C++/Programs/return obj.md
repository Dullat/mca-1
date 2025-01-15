```c++
// Online C++ compiler to run C++ program online
#include <iostream>

class stdu{
    public:
    int value;
    stdu(int value){
        this->value = value;
    }
    stdu createObj(){
        return stdu(36);
    }
};

int main() {
    stdu s1(45);
    stdu r1 = s1.createObj();
    std::cout<<r1.value;

    return 0;
}
```