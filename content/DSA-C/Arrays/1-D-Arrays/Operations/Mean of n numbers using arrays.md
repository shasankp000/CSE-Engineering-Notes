---
title: Finding the mean of n numbers using arrays -- 1-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
// Write a program to find the mean of n numbers using arrays.


#include<stdio.h>

int main() {

    int i, n, arr[20], sum = 0;

    float mean = 0.0;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    for(i=0; i<n; i++) {

        printf("\n arr[%d] = ", i);
        scanf("%d", &arr[i]);

    }

    for(i=0; i<n; i++) {

        // printf("%d \n", arr[i]);


        sum += arr[i];

    }

    mean = (float) sum/n; //typecasting int to float.

    printf("The sum of the elements is: %d \n", sum);
    printf("The mean of the elements is: %.2f", mean);

}
```
---
