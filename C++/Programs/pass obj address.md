```c++
// Online C++ compiler to run C++ program online
#include <iostream>

class stdu{
    public:
    int value;
    void show(){
        std::cout<<value;
    }
    public:
    void setValue(int x, int boolean = 0){
        value = x;
        if(boolean == 1){
            show();
        }
    }
    void modify(stdu *obj){
        obj->value = 12;
    }
};

int main() {
    stdu s1;
    s1.setValue(34,1);
    s1.modify(&s1);
    std::cout<<"\nmodified:"<<s1.value;

    return 0;
}
```