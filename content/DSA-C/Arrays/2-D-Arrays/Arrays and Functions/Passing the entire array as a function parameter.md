---
title: Passing the entire array as a function parameter -- 2-D Arrays - DSA in C
tags:
  - Semester-3
  - C
---
---
```c
// passing the entire array to the function.

#include <stdio.h>

void read_matrix(int mat[5][5], int r) {

    int i, j;
    for (i = 0; i < r; i++) {

        for (j = 0; j < r; j++) {

            if (i == j) {

                mat[i][j] = 0;

            }

            else if (i > j) {

                mat[i][j] = -1;

            }

            else {

                mat[i][j] = 1;

            }
                
        }
    };
}

void display_matrix(int mat[5][5], int r) {

    int i, j;
    for(i=0; i<r; i++) {

        printf("\n");

        for(j=0; j<r; j++) {

            printf("\t %d", mat[i][j]);

        }

    };

}

int main()
{

    int row;
    int mat1[5][5];

    printf("\n Enter the number of rows and columns of the matrix:");
    scanf("%d", &row);

    read_matrix(mat1, row);
    display_matrix(mat1, row);

    return 0;
}
```
---
