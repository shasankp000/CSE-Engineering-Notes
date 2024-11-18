---
title: " User Input in Arrays --Arrays-- Data Structures and Algorithms in C"
tags:
  - Semester-3
  - C
---
---
```c
#include<stdio.h>


// assigning values to array via user input.

int main() {


    int arr[10]; // declaring an array

    int i = 0;

    for (i; i<10; i++) {

        printf("Enter element %d: ", i);
        scanf("%d", &arr[i]); // passing a refernce to the element instead of copying iy.
        printf("\n");

    }; 


    i = 0; // resetting the counter variable to zero

    for (i; i<10; i++) {

        printf("%d \n", arr[i]); // accessing each element within the array.


    }; // Linear search algo

}
```
---
