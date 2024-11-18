---
title: " Manual value assignment  --Arrays-- Data Structures and Algorithms in C"
tags:
  - Semester-3
  - C
---
---
```c
#include<stdio.h>


// assigning values to individual elements of an array 

int main() {


    int arr1[10] = {0,1,2,3,4,5,6,7,8,9}; // declaring and assigning first array

    int arr2[10]; // declaring second array


    int i = 0; // assigning counter variable

    for (i; i<10; i++) {

        arr2[i] =  arr1[i]; // copying array1 to array2 on the individual element level

    }

    i = 0; // resetting the counter variable to zero

    for (i; i<10; i++) {

        printf("%d \n", arr2[i]); // accessing each element within the array.


    }; // Linear search algo

}
```
---
