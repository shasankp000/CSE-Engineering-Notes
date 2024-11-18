---
title: Introduction to pointers in C -- Data structures and Algorithms in C
tags:
  - Semester-3
  - C
---
---
```c
#include<stdio.h>

struct Person {

    char name[64];
    int age;

};


int main(int argc, char *argv[]) {

    // creating an array of 100 people and initializing struct on that

    struct Person people[100];
     
    // now to access and "walk" through this array, we need a pointer.

    struct Person * p_Person = &people;

    // let's loop over this array

    int i = 0;

    for (i = 0; i<100; i++) {

        p_Person->age = 0; // setting the age for every person to 0;

        p_Person += 1; // advance to the next address.

    };

    return 0;

}
```
---
