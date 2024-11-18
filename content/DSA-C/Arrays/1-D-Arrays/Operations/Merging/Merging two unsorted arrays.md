---
title: Merging two unsorted arrays -- 1-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
// Merging two unsorted arrays. Output array need not be sorted.

#include<stdio.h>

int main() {

    int arr1[10], arr2[10], arr3[20];

    int i, n1, n2, m, index = 0; 

    printf("Enter number of elements for first array: ");
    scanf("%d", &n1);
    printf("\n");

    for(i=0; i<n1; i++) {

        printf("arr1[%d] = ", i);
        scanf("%d", &arr1[i]);
        printf("\n");

    }


    printf("Enter number of elements for second array: ");
    scanf("%d", &n2);
    printf("\n");

    for(i=0; i<n2; i++) {

        printf("arr2[%d] = ", i);
        scanf("%d", &arr2[i]);
        printf("\n");

    }


    m = n1 + n2; // total number of elements in array3

    for(i=0; i<n1; i++) {

        arr3[index] = arr1[i];
        index++; // the index where iteration last stopped for array1. This will be used for continuation of insertion of elements into array3 from array2.

    } // insert elements into array3 from array1


    for(i=0; i<n2; i++) {

        arr3[index] = arr2[i];
        index++; // increments the value of index by 1 from that point onwards.

    }   // insert elements into array3 from array2

    printf("The merged array is: \n");
    
    for(i=0; i<m; i++) {

        printf("arr3[%d] = %d \n", i, arr3[i]);

    }


}
```
---
