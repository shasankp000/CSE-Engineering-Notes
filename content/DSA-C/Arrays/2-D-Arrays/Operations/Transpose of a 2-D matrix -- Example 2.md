---
title: Transpose of a 2-D matrix -- Example 2 -- Arrays -- Data Structures and Algorithms in C
tags:
  - Semester-3
  - C
---
---
```c
#include <stdio.h>

int main()
{

    int i, j, mat[3][3], transposed_mat[3][3];

    printf("\n Enter the elements of the matrix: ");

    for (i = 0; i < 3; i++) {

        for (j = 0; j < 3; j++) {

            scanf("%d", &mat[i][j]);
  
        }
    }

    printf("\n The elements of the matrix are ");

    for (i = 0; i < 3; i++) {

        printf("\n");

        for (j = 0; j < 3; j++) {

            printf("\t %d", mat[i][j]);

        }
            
    }

    for (i = 0; i < 3; i++) {

        for (j = 0; j < 3; j++) {

            transposed_mat[i][j] = mat[j][i];

        }
            
    }

    printf("\n The elements of the transposed matrix are ");

    for (i = 0; i < 3; i++) {

        printf("\n");

        for (j = 0; j < 3; j++) {

            printf("\t %d", transposed_mat[i][j]);

        }

    }
    return 0;
}
```
---
