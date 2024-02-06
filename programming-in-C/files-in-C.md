# Working with files in C

## text files

Read the file: `"r"`
```c
file = fopen("file_name.txt", "r");
if (file == NULL) {
    fprintf(stderr, "Error opening file\n");
    return 1;
}
return 0;
```

Open file for writing: `"w"`
```c
FILE *file
file = fopen("file_name.txt", "w");
if (file == NULL) {
    fprintf(stderr, "Error opening file\n");
    return 1;
}
return 0;
```
or use `"a"` to append to the file instead of editing

Writing to the file:
```c
fprintf(file, "message\n");
```
*Note: use `fprintf()` carefully*

In the end, remember to clse the file
```c
error = fclose(file);
if (error != 0) {
    fprintf(stderr, "fclose failed\n");
    return 1;
}
return 0;
```

## binary files

Binary files are not human-readable

A few ways to open a binary file:

```c
binary = fopen("binary.txt", "rb");
binary = fopen("binary.dat", "wb");
binary = fopen("binary", "wb");
binary = fopen("binary.mp3", "ab+");
```

### writing binary files

We need to use `fwrite()` to write to the binary files. The format is different from `fprintf()` when writing text files.
```c
size_t fwrite(const void *ptr, size_t size, size_t nmemb, FILE *stream);
```
`*ptr`: pointer to the data that we want to write to the file
`size`: size of each element that are writing to the rile
`nmemb`: number of elements
`*stream`: file pointer to the file we are writing
* must refer to a stream open in binary mode

If a `fwrite()` call returns 0, an error has occured and no items were successfully written on that call.

### reading binary files

`fread()` must follow the order of how we initialize the variables.

If a `fread()` call returns 0, it marks the end of the file and no items were successfully read on that call (possibly an error).

