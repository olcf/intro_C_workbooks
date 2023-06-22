### <a name="dt"></a>2. Data Types
Variables are named storage areas

For example, `int a = 5` creates a variable (storage area in memory) named “a” and saves the value of 5 in that memory location.

Variables of different data types occupy different amounts of memory and can store different ranges of values, and these variables must be declared before use.

### <a name="bdt"></a> Basic Data Types

| Name          | Type          | Range of Values | Size (B) |
| ------------- | ------------- | -------------   | -------------   |           
| Char          | Character     | ASCII Characters| 1  |
| Int		 | Integer   | -2,147,483,648 to 2,147,483,647   | 4 |
| Float  | Decimal (precision to 6 places)   | 1.2e-38 to 3.4e38   | 4 |
| Decimal  | Decimal (precision to 15 places)   | 2.3e-308 to 1.7e308   | 8 |

### <a name="pf"></a> Printf Function
#### Formatted Output with `printf` function
<ins>Example 1</ins>:

Code:
```
printf("Hello World");
```
Output:
```
 $ ./a.out
Hello World$
 ```
Result: Hello World

<ins>Example 2</ins>:

Code:
```
printf("Hello World\n");
```
Output:
```
 $ ./a.out
Hello World
$
 ```
Result: Hello World (with a new line)

### Format Tags: represented by a percent sign (%) followed by a character that specifies the type of formatting
* %c: Character
* %d: Integer
* %f: Floating-point number
* %s: String

 <ins>Example 3</ins>: 
```
int i = 2;
printf(“The value of the integer is %d\n”, i);
```
* i represents the variable whose value is used in the format tag

Result: The value of the integer is 2
 
 <ins>Example 4</ins>:
 ```
float x = 3.14159;
printf(“The value of the float is %.2f\n”, x);
```
* x represents the variable whose value is used in the format tag

Result: The value of the float is 3.14

There is a code called data.c that you can use to explore the data types. 

To compile the C program, use the gcc compiler to compile the C code into an executable:

```
$ gcc -o data data.c
```
-o is compiler flag that allows you to name the executable.

List the directory using `ls` to verify your `data` executable was created. 

Then do:

```
$ ./data
```
to run the program. 

Once you see that it ran, use `vi` to view the code and play with the variables. Remember to recompile with each change. 

