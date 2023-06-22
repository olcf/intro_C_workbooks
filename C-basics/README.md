## The C Programming Language 

C is a general programming language initally deveopled by Dennis Ritchie at Bell Laboratories. 
It is a compiled language, which means that a program called a compiler is used to translate the code that you write in C into 
machine langauge that your computer can use. 

Many operating systems and scripting programming language are written with C. Examples include Perl, PHP, Python and Ruby. 

C is one of the most common prgramming languages used for High Performace Computing. 

Here is a simple example to show the very basics of C. 

```
/*------------------------------------------------------------
Program that prints that value of an integer to the screen.
------------------------------------------------------------*/

#include <stdio.h>

int main(){

    int a = 3;
    printf("The value of this integer is %d\n", a);

    return 0;
}

```
The `#include <stdio.h>` statement is a C preprocessor directive telling the compiler to include contents of the header file in angle brackets.

The `int main()` is a declaration of a function called main, which is where the execution of the program begins.  `main` is included in all C programs. The “int” indicates that the function will return an integer value.

`{` and `}` are curly braces that indicate the beginning and end of the main function.

`int a = 3` defines an integer called “a” and assigns it a value of 3.

`;` is a semicolon used to indicate the end of each statement.

`printf` is a function that sends formatted output to stdout (typically the terminal from which the program was run). Stdout refers to standard output, and when the user runs the program, it prints the output data to the display screen. `printf` is defined in the stdio.h header file, which includes the standard input/output functions. 

`return 0` is a return value “returned” to the run-time environment. Typically, a value of 0 indicates a normal/successful exit.

To compile the C program, use the gcc compiler to compile the C code into an executable:
```
$ gcc simple.c
```

An executable is named a.out by default. To view the list of files in a current directory, use the `ls` command: 
```
$ ls
a.out  simple.c
```

To run the program, use the following:
```
#./a.out
The value of this integer is 3
```
Specifying `./` before the command or program name indicates that the program should be found and executed in the current directory.

<ins>To specify Output File Name </ins>:
To compile the C program, use the gcc compiler to compile the C code into an executable:
```
$ gcc -o simple simple.c
```
-o is compiler flag that allows you to name the executable

To view the list of files in the directory:
```
$ ls
simple  simple.c
```
Run the program:
```
#./simple
The value of this integer is 3
```
This tutorial was made by Gladys Chen based on Tom Papatheordore's slides and notes. 
