
![](https://youtu.be/mB5HXBb_HY8?si=0qQKLYJ6e-gg7Xld)
### 1. Introduction to Merge Sort

Start with a brief explanation of merge sort:

- **Definition**: Merge Sort is one of the most popular [sorting algorithms](https://www.programiz.com/dsa/sorting-algorithm) that is based on the principle of [Divide and Conquer Algorithm](https://www.programiz.com/dsa/divide-and-conquer).

Here, a problem is divided into multiple sub-problems. Each sub-problem is solved individually. Finally, sub-problems are combined to form the final solution.

[full explanation](https://www.programiz.com/dsa/merge-sort)

![[Pasted image 20240910113248.png]]

## Divide and Conquer Strategy

Using the **Divide and Conquer** technique, we divide a problem into subproblems. When the solution to each subproblem is ready, we 'combine' the results from the subproblems to solve the main problem.

Suppose we had to sort an array A. A subproblem would be to sort a sub-section of this array starting at index p and ending at index r, denoted as A[p..r].

**Divide**

If q is the half-way point between p and r, then we can split the subarray A[p..r] into two arrays A[p..q] and A[q+1, r].

**Conquer**

In the conquer step, we try to sort both the subarrays A[p..q] and A[q+1, r]. If we haven't yet reached the base case, we again divide both these subarrays and try to sort them.

**Combine**

When the conquer step reaches the base step and we get two sorted subarrays A[p..q] and A[q+1, r] for array A[p..r], we combine the results by creating a sorted array A[p..r] from two sorted subarrays A[p..q] and A[q+1, r].

### Algo

> [!NOTE]
> MergeSort(A, p, r):
>     if p > r 
>         return
>     q = (p+r)/2
>     mergeSort(A, p, q)
>     mergeSort(A, q+1, r)
>     merge(A, p, q, r)

### Time complexity
Discuss the time complexity of merge sort:

- **Best, Average, and Worst Case**: All are O(nlog⁡n)O(n \log n)O(nlogn).
- **Space Complexity**: O(n)O(n)O(n) due to the additional space used for temporary arrays.

### Program

```
#include <iostream>

int merge(int arr[], int left, int mid, int right){
    int tempArrIndex1 = mid - left + 1; // right sub array
    int tempArrIndex2 = right - mid; // left sub array
    int tempArr1[100];
    int tempArr2[100];
    
    for(int i = 0; i <= tempArrIndex1; i++){
        tempArr1[i] = arr[left + i];
    }
    
    for(int j = 0; j <= tempArrIndex1; j++){
        tempArr2[j] = arr[mid + 1 + j];
    }
    
    int i = 0, j = 0, k = left;
    
    while(i < tempArrIndex1 && j < tempArrIndex2){
        if(tempArr1[i] <= tempArr2[j]){
            arr[k] = tempArr1[i];
            i++;
        }else{
            arr[k] = tempArr2[j];
            j++;
        }
        k++;
    }
    
    while (i < tempArrIndex1) {
        arr[k] = tempArr1[i];
        ++i;
        ++k;
    }

    while (j < tempArrIndex2) {
        arr[k] = tempArr2[j];
        ++j;
        ++k;
    }
    
    return 0;
}

int mergeSort(int arr[], int left, int right){
    if(left < right){
        int mid = (left + right) / 2;
        
        mergeSort(arr, left, mid);
        mergeSort(arr, mid+1, right);
        
        merge(arr, left, mid, right);
    }
    return 0;
}

int main() {
    int arr[] = {14, 7, 3, 12, 9, 11, 6, 2, 9};
    int p = 0;
    int r = sizeof(arr) / sizeof(arr[0]); 
    
    mergeSort(arr, p, r - 1);
    
    for(int i = 0; i < r; i++){
        std::cout<<arr[i]<<"\n";
    }

    return 0;
}
```