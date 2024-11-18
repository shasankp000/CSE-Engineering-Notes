---
title: Inserting is done such that the array remains sorted in ascending order -- 1-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
// inserting is done such that the array remains sorted in ascending order.

#include<stdio.h>

int main() {

    int arr[20];

    int i, j, n, num, pos = 0;


    printf("Enter number of elements: ");
    scanf("%d", &n);

    for(i=0; i<n; i++) {

        printf("\n arr[%d] = ", i);
        scanf("%d", &arr[i]);

    }

    printf("Enter the element which is to be entered: ");
    scanf("%d", &num);
    printf("\n");


    for(i=0; i<n; i++) {

        if (arr[i]>num) {

            pos = i; // position for that element to be inserted is that index. 

            for(j=(n-1); j>=pos; j--) {

                arr[j+1] = arr[j]; // shifting all elements from that position onwards to make space for the new element.   

            }

            arr[pos] = num; // assigning the new element to that position.


            break; // exiting the outer loop;

        }

    } 

    n = n+1; // increasing the total number of elements by 1.

    printf("The array after insertion of %d is : ", num);

    printf("\n");

    for(i=0; i<n; i++) {

        printf("arr[%d] = %d \n", i, arr[i]);

    }


}
```
---