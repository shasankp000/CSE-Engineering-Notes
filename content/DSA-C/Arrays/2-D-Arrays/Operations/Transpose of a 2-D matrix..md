---
title: Transpose of a 2-D matrix -- Arrays -- Data Structures and Algorithms in C
tags:
  - Semester-3
  - C
---
---
```c
// Transpose of a 2-D matrix. Just interchange the rows and columns.

#include<stdio.h>

struct Matrix {

    int rows;
    int cols;

    int(*set_r_c)(struct Matrix *, int, int);


};

int set_rows_cols(struct Matrix * inst, int rows, int cols) {

    inst->rows = rows; // updating the values to the struct.
    inst->cols = cols;

    printf("%d %d", rows, cols);

}; // setter function.


int transpose(struct Matrix * inst ,int mat[inst->rows][inst->cols]) {

    int k, l;

    int new_rows = inst->cols;

    int new_cols = inst->rows;

    int transposed_mat[new_rows][new_cols]; // new matrix with interchanged rows and cols

    for(k=0; k<new_rows; k++) {

        for(l=0; l<new_cols; l++) {

            transposed_mat[k][l] = mat[l][k];

        };

    };

    printf("The elements of the transposed element are: ");

    for(k=0; k<new_rows; k++) {

        for(l=0; l<new_cols; l++) {

            printf("%d \t", transposed_mat[k][l]);

        };

    };

} ;


int main() {

    int r, c;

    printf("Enter the rows and columns of the matrix: ");
    scanf("%d %d", &r, &c);
    printf("\n");

    int i, j, mat[r][c]; // taking a 3 by 3 matrix for reference purpose.

    int t_mat[c][r];

    printf("Enter the elements of the matrix \n");
    for(i=0; i<r; i++) {

        for(j=0; j<c; j++) {

            scanf("%d", &mat[i][j]);
            printf("\n");

        };

    };

    struct Matrix m;

    m.set_r_c = set_rows_cols;


    m.set_r_c(&m, r, c);
 
  
}
```
---
