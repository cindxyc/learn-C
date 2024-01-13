# Command lines for Mac Terminal

Open the directory that we want to work with (source code file):
```console
cd directory
```
Check the current working directory:
```console
ls
```
To compile the file, let's say, the file `program.c`. This line tells the compiler to read our file, and produce and executable file that we can run
```console
gcc program.c
```

When we check the current working directory again, we will see that a new executable file is added that ends in `.out`.

To run the file simply type `./` in front of the name of the file.

```console
./xxx.out
```