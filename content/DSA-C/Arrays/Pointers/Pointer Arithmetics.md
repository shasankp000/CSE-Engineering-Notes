---
title: Pointer Arithmetics -- Data Structure and Algorithms in C
tags:
  - Semester-3
  - C
---
---
```c
#include<stdio.h>

int main() {

    int a = 34;

    int *ptr_a = &a; // storing the address of a;

    printf("%d \n", ptr_a);
    printf("%d", ptr_a+1); // adds the value of ptr_a with a sizeof(type), in this case, int.

    // value of sizeof(int) varies on different architectures.

    return 0;
}
```
---
