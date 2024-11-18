---
title: Array element as a parameter to a function argument -- 1-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
#include<stdio.h>

// case 1: passing data values

int fun1(int num) {

    printf("%d", num);

}


int main() {

    int arr[5] = {1, 2, 3, 4, 5};

    fun1(arr[4]);


}
```
---
