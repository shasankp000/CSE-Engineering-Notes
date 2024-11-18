---
title: Pointers in 2-D arrays  --Arrays-- Data Structures and Algorithms in C
tags:
  - Semester-3
  - C
---
---
To understand this, view the section first.

```c
#include <stdio.h>

void display(int (*mat)[3])
{
    int i, j;
    printf("\n The elements of the matrix are: ");
    for (i = 0; i < 3; i++)
    {
        printf("\n");
        for (j = 0; j < 3; j++)
            printf("\t %d", *(*(mat + i) + j));
    }
}

int main()
{
    int i, j, mat[3][3];
    printf("\n Enter the elements of the matrix: ");
    for (i = 0; i < 3; i++)
    {
        for (j = 0; j < 3; j++)
        {
            scanf("%d", &mat[i][j]);
        }
    }
    display(mat);

    return 0;
}
```
---
