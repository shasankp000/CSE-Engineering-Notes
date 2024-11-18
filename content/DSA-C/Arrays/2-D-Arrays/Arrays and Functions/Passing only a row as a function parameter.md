---
title: Passing only a row as a function parameter -- 2-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
// passing only a row.

#include<stdio.h>

void func(int arr[]) {

    int i;
    for (i=0; i<3; i++) {

        printf("%d", arr[i] * 1 );

    }

}



int main() {

    int arr[2][3] = {{1, 2, 3}, {4, 5, 6}};



}
```
---
