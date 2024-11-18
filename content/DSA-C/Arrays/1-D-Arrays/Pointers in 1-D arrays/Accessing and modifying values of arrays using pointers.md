---
title: Value reading and modification via pointers -- 1-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
----
```c
#include<stdio.h>

// accessing and modifying values of array elements using pointers.

int main() {

    int arr[]={1,2,3,4,5};

    int *ptr, i;

    ptr=&arr[2]; // points to the address of arr[2]

    *ptr = -1; // to access and change the value of arr[2] *ptr has to be used

    *(ptr+1) = 0; // accesses the next element and changes it's value.

    *(ptr-1) = 1; // accesses the previous element and changes it's value.

    printf("\n Array is: ");

    for(i=0;i<5;i++) {

        printf(" %d", arr[i]);

    }

    return 0;


}
```
---
