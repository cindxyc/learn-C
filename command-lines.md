# Command lines for Mac Terminal

## Start working with our files

Open the directory that we want to work with (source code file)
change directory
```console
cd ...\Users\file\...
```

Check the current working directory
list files in directory
```console
ls
```

make a new directory
```console
mkdir
```

copy a file
```console
cp
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

Running `ls -F` can check if a file is an executable file. There will be a star `*` following the file. For example, `xxx.out*`


## Compiling the file

```console
gcc -Wall -o program program.c
```
Other than just compiling, `Wall` will give you any warning messages that your code
`-o` allows you to specify the name of the executable file where `gcc` will save its output. In this case, we get a new executable file name `program` that if you run `./program`, it gives the same output as before.


## Permission of the file

To check the permission, use the command line

```console
ls -l
```

The output looks like this:
```console
drwxr-x--- 4   root cdfstaff 4096  Nov 20 13:30 boot/
dr-xr-xr-x 2   root root     4096  Sep 6  13:26 cdf/
drwxr-xr-x 17  root root     4340  Nov 13 10:26 dev/
drwxr-xr-x 179 root root     12288 Nov 23 08:49 etc/
drwxr-xr-x 2   root root     4096  Apr 18 2022  home/
```

The first column formatted in `rwxrwxrwx` shows the permissions. `drwxrwxrwx` marks a directory and `-rwxrwxrwx` is just a regular file.
Each `rwx` means user/owner, group and other.

We can change the file permissions by using the command `chmod 755 <filename>`.