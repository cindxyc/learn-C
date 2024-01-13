# How to use print function in C

## Print "Hello World"
C program first needs to be given a package that includes the functions to be used

Here, `printf()` is classified as an Input Output function, so we have to include a "Standard Input Output" package

```c
#include <stdio.h>
```

Next, we need a class to contain the function.
```c
int main () {
    
    printf("hello world\n");

    return 0;
}
```

Output:
```c
hello world
```

`\n` marks the end of line, any extra `\n` will give new empty lines.

In C programming, the `return 0` statement is typically used at the end of the `main` function to indicate a successful termination of the program.


## Printing Numbers

In C, we can make the `printf()` function to call a variable that we declared. Inside of `printf()`, we use `%d` to tell the program to replace with an int.

For example:
```c
int main () {
    int num = 13;
    printf("Taylor's fav number: %d\n", num);

    return 0;
}
```

Output:
```c
Taylor's fav number: 13
```

If we want to use a float, declare the variable

```c
double floatNum = 2.2;
```

Then use `%f` instead of `%d`.


Multiple variables is possible as well. To do this, just make sure that the variables are in order as wanted.

For example:
```c
int main () {
    int num1 = 1;
    int num2 = 2;
    printf("prints two numbers %d and %d:", num1, num2);  // the output depends on how you order the two variables
    
    return 0;
}
```

Output:
```c
prints two numbers 1 and 2
```