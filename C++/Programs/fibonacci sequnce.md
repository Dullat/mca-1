```
#include <iostream>

int main() {
    int n[100];
    int len = 30;
    
    for(int i = 0; i < len; i++){
        if(i == 0){
            n[i] = 0;
            continue;
        }
        if(i == 1){
            n[i] = 1;
            continue;
        }
        n[i] = (n[i - 1]) + (n[i - 2]);
    }
    
    int counter = 0;
    while(counter < len){
        std::cout<<n[counter]<<"\n";
        counter++;
    }

    return 0;
}
```