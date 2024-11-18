---
title: Array with pointers as elements -- 1-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
// array of pointers.

#include<stdio.h>

int main() {

    int arr1[]={1,2,3,4,5}; // array 1
 
    int arr2[]={0,2,4,6,8}; // array 2

    int arr3[]={1,3,5,7,9}; // array 3

    int *parr[3] = {arr1, arr2, arr3}; // pointer array of 3 elements where the elements are addresses pointing to each array's first element.

    int i;
    for(i = 0;i<3;i++) {

        printf("%d \n", *parr[i]);

    };

    return 0;

}
```
---
