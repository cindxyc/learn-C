# Useful C Features

## typedef

`typedef` creates an alias for an existing type.

`typedef` can be used with `struct`, making code easier to read.

Example:

```c
typedef struct {
    char name[20];
    int age;
} Person;

Person person;
Person *p;
```

## macro - `#define`