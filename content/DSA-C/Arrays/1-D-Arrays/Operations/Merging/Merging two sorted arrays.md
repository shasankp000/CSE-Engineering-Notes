---
title: Merging two sorted arrays, output array needs to be sorted -- 1-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
// Merging two sorted arrays. Output array has to be sorted.

#include<stdio.h>

int main() {

    int arr1[10], arr2[10], arr3[20];

    int i, n1, n2, m, index = 0; 

    int index_first = 0, index_second = 0; // indexes of first and second array respectively

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

    m = n1+n2;

    while(index_first < n1 && index_second <n2) {

        if (arr1[index_first] < arr2[index_second]) {

            arr3[index] = arr1[index_first];
            index_first++;

        } // if the given index of first array is less than second array, append it to third array.

        else {

            arr3[index] = arr2[index_second];
            index_second++;

        } // append the given index of second array to the third array.

        index++; // increase the index value of the third array.

    }


    // if the elements of first array are over and the second array has some elements left.

    if (index_first == n1) {

        while (index_second<n2) {

            arr3[index] = arr2[index_second];
            index_second++;
            index++;

        }

    }

    else if (index_second == n2) {

        while (index_first<n1) {

            arr3[index] = arr1[index_first];
            index_first++;
            index++;

        }

    }

    printf("The merged array is: \n");

    for(i=0; i<m; i++) {

        printf("arr3[%d] = %d \n", i, arr3[i]);

    }


}
```
---
