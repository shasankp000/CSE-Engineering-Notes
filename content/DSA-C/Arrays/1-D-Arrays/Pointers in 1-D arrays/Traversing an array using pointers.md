---
title: Traversal of an array via pointers -- 1-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
#include<stdio.h>

// traversing an array using only pointers.

int main() {

    int arr[] = {1,2,3,4,5,6,7,8,9};

    int *ptr1, *ptr2;

    ptr1 = arr; // pointing to arr[0], same as ptr1 = &arr[0]

    ptr2 = &arr[8]; // pointing to the address of the last element of arr

    while(ptr1<=ptr2) {

        printf("%d \n", *ptr1); // to access the value, we use *ptr1
        ptr1++; // points to the address of the next element in arr, i.e arr[1], arr[2] and so on until arr[8]

    };


}
```
---
