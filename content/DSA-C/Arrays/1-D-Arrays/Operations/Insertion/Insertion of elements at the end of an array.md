---
title: Insertion of elements at the end of an array -- 1-D Array -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
// inserting at the end of an array

#include<stdio.h>

int main() {

    int arr[10] = {0,1,2,3,4,5}; // array with 6 elements.

    arr[6] = 6; // appending a new element at the end.


    int i = 0;

    for(i; i<=6; i++) {

        printf("%d \n", arr[i]);

    }


}
```
---
