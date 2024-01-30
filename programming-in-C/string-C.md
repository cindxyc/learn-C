# String in C

## Null-terminated string
A `char` array that must end with a null character `'\0`


Ways to present a string literal:
```c
char str[] = {'h', 'e', 'l', 'l', 'o', '\0'};
char str[] = "hello";
```

## Allocating String

On the **stack**:
```c
char str[13] = "hello";
```

On the **heap**:
```c
char *str = malloc(sizeof(char)*13);
strcpy(str, "hello"); //copying "hello" into str
```

**String literals** Read-only data section:
```c
const char *str = "hello";
```

