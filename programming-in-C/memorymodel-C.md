# Memory Array in C


## Buffer
Stores variables that are close to but not 0.
Example: `NULL`

## Code
Where the code is stored once the file is compiled into machine instructions.
\* *Note: array starts at 0, but the code segment is close to but NOT at 0*

## Global Data
Data outside of the functions, is allocated for the entire program.

Example code:
```c
int ab(int a, int b) {
    int i;
    i = a + b;
    return i;
}
int z;
int main() {
    z = ab(1, 3);
    return 0;
}
```
Here in our example code, `int z` is a global value.
Some other global data include but not limited to: pointers

## Heap
Dynamically allocated memory, with longer lifetime than the function. Keeps the data until we explicitly deallocate it (`free()`).
\* *NOTE: must deallocate memory after use*
```c
void *malloc(size_t size);
```
`void *` pointer is used to return a pointer of a generic type
`malloc` returns `void *`, the address of the memory that is allocated
where `size` indicates the amount of memory (bytes) should be allocated

An example to use:
Original code:
```c
int *set_i() {
    int i = 13;
    return &i;
}

int other() {
    int other = 22;
    return other;
}

int main() {
    int *num = set_i();
    printf("*num is now %d\n.", *num);
    return 0;
}
```
Here, the output would be
```c
*num is now 22.
```
This is because `other` is the last value in the stack as `*set_i()` is already popped out. Therefore any value defined in the function `*set_i()` will not be kept after `*set_i()` is executed, which means when `main()` runs, `*num` will not have any value.

Fixed code:
```c
int *set_i() {
    int *i = malloc(sizeof(int));
    *i = 13;
    return i;
}

int main() {
    int *num = set_pointer();
    printf("*num is now %d\n", *num);
    return 0;
}
```
Now the output is
```c
*num is now 13.
```
as wanted.

## Free space
Small space that seperates `Heap` and `Stack`

## Stack
Stores local variables, infomation about a function call.
* Automatically allocated when functions are called
* Automatically deallocated when functions return
* \*Function calls are removed in last in first out order (growing up visually)
\* *NOTE: local variables cannot be accessed after function ends, its lifetime is inside the bracket they belong to*

Example code:
```c
int sum(int a, int b) {
    int i;
    i = a + b;
    return i;
}
int z;
int main() {
    z = sum(1, 3);
    return 0;
}
```
Order:
1. stack frame: local variables & arguments
```c
int a, int b, int i
```
Once excuted, the stack frame is popped and return the value (`int i`) to the caller (`main`)
\* *Note: only accessible when the function that defines them is active*

2. function currently being executed: `main`
Is the first stack once local variables are popped out.

## OS

\* `seg fault` when you try to access some OS data which you don't have access to