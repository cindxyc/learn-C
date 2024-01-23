# Array in C

## Declare an array

In C, an array is initialized with a size. General Syntax:
```c
datatype array_name[size] = {elements};
```

`datatype`: type of the element stored in the array, such as `int`, `float`, `char`, or `double` data

`[]`: # of elements stored

`{}`: initializer list

## Ways to initialize an array

An array of size n:
```c
int array[n];
```
An array that its size depends on the initializer list and can be changed:
```c
int array[] = {1, 9, 8, 9};
```
Set all elements in the array to one value:
```c
int array[13] = {0};
```
Initialized the first few elements:
```c
int array[13] = {1, 3};
```

## Array decay
When an array is passed to function, for example, `printf(“%lu\n”, array)`, array becomes the pointer to the first element. In other words, it will only use the first element of the array.

To work with the entire array, we need to pass the size of the array to the function:
```c
void print_array(int size, const int arr[size]) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
```
*Important: In the function parameter, `size` as an `int` needs to be placed before the array.*


## Const Correctness

When working with arrays in C, it is possible that the arrays are modified after being passed to a function. The qualifier `const` helps to prevent modifications and make the shit read-only.


## Allocating Array

Suppose we have two arrays `l1` and `l2` and we want to allocating them using pointers.
```c
int l1[] = {x, ...};
int l2[] = {x, ...}; // we don't know the size
```

Step 1: Define the pointers
```c
int **pointers = malloc(sizeof(int*) * num);
```
`**pointers`: we need one allocating the item (array), and another one allocating to the `int` (inside of the array)
`malloc(sizeof(int*) * num)`: here we have 2 arrays, so in fact the code is `malloc(sizeof(int*) * 2)` if we have more, adjust it according the number of arrays we have

Step 2: For each pointer allocating the item, define its size according to the array length
```c
pointer[0] = malloc(sizeof(int*) * length);  // need a free() statement later
pointer[1] = malloc(sizeof(int*) * length);  // need a free() statement later
...
```
`length`: size of the array

Step 3: Assign the integers
```c
pointer[0][0] = x;
pointer[0][1] = y;
...
```

Lastly: Freeing the pointers
Due to the structure of arrays, we cannot free the entire pointer at once. Moreover, we need to free the sublist of arrays in order beforehand.
In other words, each `malloc()` should have a corresponding `free()` statement.

```c
free(pointers[0]);
free(pointers[1]);
free(pointers);
```