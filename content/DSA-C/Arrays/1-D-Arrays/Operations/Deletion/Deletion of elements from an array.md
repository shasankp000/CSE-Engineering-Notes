---
title: Deletion of elements from an array -- 1-D array -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
#include <stdio.h>
#include <stdlib.h>
int main() {
    
    int *arr; // array pointer

    int size = 10; // declare array size.

    arr = (int *)calloc(size, sizeof(int)); // allocate memory for the array.


    int i, n, pos, arr2[10];

    printf("Enter number of elements: ");
    scanf("%d", &n);

    for(i=0; i<n; i++) {

        printf("\n arr[%d] = ", i);
        scanf("%d", &arr[i]);

    }

    printf("\nEnter the position from which the number has to be deleted : ");
    scanf("%d", &pos);

    for(i=pos; i<n-1;i++) {
        arr[i] = arr[i+1];
    }

    n--;

    for(i=0; i<n; i++) {

        arr2[i] = arr[i]; // populate the second array with the intended number of elements.

    }

    free(arr); // free the memory occupied by the array.

    printf("\n The array after deletion is : ");
    for(i=0;i<n;i++) {

        printf("\n arr2[%d] = %d", i, arr2[i]);

    }


}
```
---
