---
title: Insertion of elements at any index in an array -- 1-D Array -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
// inserting at any index

#include<stdio.h>

int main() {

    int arr[20];

    int i, n, num, pos = 0;


    printf("Enter number of elements: ");
    scanf("%d", &n);

    for(i=0; i<n; i++) {

        printf("\n arr[%d] = ", i);
        scanf("%d", &arr[i]);

    }

    printf("Enter the element which is to be entered: ");
    scanf("%d", &num);
    printf("\n");

    printf("Now enter it's position: ");
    scanf("%d", &pos);
    printf("\n");

    for(i=(n-1); i>=pos; i--) {

        arr[i+1] = arr[i];

    } // shifting all elements from that position onwards to make space for the new element.   

    arr[pos] = num; // assigning the new element to that position.

    n = n+1; // increasing the total number of elements by 1.

    printf("The array after insertion of %d is : ", num);

    printf("\n");

    for(i=0; i<n; i++) {

        printf("arr[%d] = %d \n", i, arr[i]);

    }


}
```
---
