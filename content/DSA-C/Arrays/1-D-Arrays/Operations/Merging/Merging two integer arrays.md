---
title: Merging two integer arrays -- 1-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
#include<stdio.h>
#include<stdlib.h>

// Finalised and imrproved version of merging two integer arrays.

int main() {

    int size = 10;

    int *arr1, *arr2;

    arr1 = (int *)malloc(size * sizeof(int));
    arr2 = (int *)malloc(size * sizeof(int));

    int i, j, n1, n2,tracker, m = 0;

    printf("Enter number of elements for first array: ");
    scanf("%d", &n1);
    printf("\n");

    for(i=0; i<n1; i++) {

        printf("arr1[%d] = ", i);
        scanf("%d", &arr1[i]);
        printf("\n");

    }

    tracker = i; // stores where the last element was entered in arr1.

    printf("Enter number of elements for second array: ");
    scanf("%d", &n2);
    printf("\n");

    for(i=0; i<n2; i++) {

        printf("arr2[%d] = ", i);
        scanf("%d", &arr2[i]);
        printf("\n");

    }

    m = n1+n2;

    // append elements from arr2 to arr1

    j = 0;

    for(i=tracker; i<m; i++) {

        arr1[i] = arr2[j];
        j++;

    }

    printf("The merged array is: \n");

    for(i=0; i<m; i++) {

        printf("arr3[%d] = %d \n", i, arr1[i]);

    }


    // cleanup 

    free(arr1);
    free(arr2);



    return 0;
}
```
---
