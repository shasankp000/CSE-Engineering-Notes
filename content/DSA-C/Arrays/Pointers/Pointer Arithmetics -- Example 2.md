---
title: Pointer Arithmetics -- Example 2 -- Data Structure and Algorithms in C
tags:
  - Semester-3
  - C
---
---
```c
#include<stdio.h>

int main() {

    int arr[] = {1,2,3,4,5,6,7};
    int *arrayptr = arr; // making a pointer which points to arr.

    printf("Value at position 3 of the array is %d\n", arr[3]);
    printf("Address of position 3 of the array is %d\n", &arr[3]);
    printf("Address of position 3 of the array is %d\n", arr + 3);

    printf("The value at address of position 3 of the array is %d\n", *(&arr[3])); // dereferencing
    printf("The value at address of position 3 of the array is %d\n", *(arr + 3)); // method 2

    printf("Address of position 0 of the array is %d\n", arrayptr);
    printf("Address of position 1 of the array is %d\n", arrayptr+1);
    printf("Value of position 0 of the array is %d\n", *arrayptr);
    printf("Value of position 1 of the array is %d\n", *arrayptr+1);

    // arrayptr++;  // is valid, arr++ is not.

    return 0;
}
```
---
