# Array in C

## Declare an array

In C, an array is initialized with a size. General Syntax:
```c
datatype array_name[size] = {elements};
```

`datatype`
* type of the element stored in the array, such as `int`, `float`, `char`, or `double` data
`[]`
* \# of elements stored
`{}`
* initializer list

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
To work with the entire array, we need to pass the size of the array to the function `printf(“%lu\n”, array[size])`
```c
void print_array(int size, const int arr[size]) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
```
In the function parameter, size as an int needs to be placed before the array


## Const Correctness

When working with arrays in C, it is possible that the arrays are modified after being passed to a function. The qualifier `const` helps to prevent modifications and make the shit read-only.