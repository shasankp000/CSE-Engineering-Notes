---
title: Address of array element as a parameter to a function -- 1-D Arrays -- DSA in C
tags:
  - Semester-3
  - C
---
---
```c
#include<stdio.h>

// case 2: passing addresses of data values

int fun1(int *num) { // since addresses must be passed by a reference which are really just pointers.

    printf("%d", *num);

}


int main() {

    int arr[5] = {1, 2, 3, 4, 5};

    fun1(&arr[4]); // passing reference to the address of the value.

    return 0;
}
```
---
