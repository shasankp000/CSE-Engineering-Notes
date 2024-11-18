---
title: 2D Array -- Arrays -- Data Structures and Algorithms in C
tags:
  - Semester-3
  - C
---
---
```c
#include <stdio.h>

int main() {

    //initialize 2d array.

    // <type> <arr><rows><columns> = {{row1, col1, ....}, {row2, col2, ....}}

    int arr[2][2] = {{12,34}, {56, 32}}; // 2d array initialized

    int i, j; // counter variables

    for (i=0; i<2; i++) { // accessing 1d

        printf("\n");

        for(j=0; j<2; j++) { 
            printf("%d\t", arr[i][j]); // accessing 2d or the innermost array.
        }


    };


}
```
---
