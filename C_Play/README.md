
                                                                               
                               $$$$$$$$$$$$$$$$                                
                           $$$$####********####$$$                             
                         #####******************#####                          
                       ####**!!*!!!!======!!!!*!!**###*                        
                      ******!!!==;;::::::::;;==!!!******                       
                     ****!!!!==;:~~--,,,,--~~:;==!!!!****                      
                    !****!!!=;:~--..........--~:;=!!!****!                     
                    !!!!!!!=;;:-,............,-:;;=!!!!!!!                     
                   ;!!!!!!==;:~-...        ...-~:;==!!!!!!;                    
                   ;!!!!!!!=;;~-,.          .,-~;;=!!!!!!!;                    
                   ;=!!!!!!===;;;~          ~:;====!!!!!!=:                    
                    ==!!!!!!!!!!!!=        =!!!!!!!!!!!!==                     
                    ;==!!!!*****######**######*****!!!!==:                     
                     ;==!!!!**###$$$$@@@@$$$$###**!!!!==;                      
                     -:;=!!!***###$$$$@@$$$$###***!!!=;:-                      
                       ~;==!!!!***###$$$$####**!*!!==;:                        
                        -:;==!!***!*********!**!!==;:-                         
                          ,~:;==!!!!******!!!!=;;:~,                           
                             ,-~::;;==;;==;;::~-,                              
                                  ..,,,,,,..          


**Goals**
* Learn to compile and run a C-code.
* Play with a few basic coding structures in C.
* Identify and begin to understand how to read `for loops` in C.

***Git the Repo***

Login to the open DTN or ascent and clone this repository in your home area if you have not already done so. 

Login help: See slide 10 : https://docs.google.com/presentation/d/1xUCsLPY6ehkugdraxgoWCLAmrkWOod6IT0S07BYeDIg/edit?usp=sharing

To clone: 

```
$ git clone https://github.com/olcf/intro_C_workbooks.git

```

We will use Unix commands to change to the directory where the code is. 

```
$ cd intro_C_workbook/C_Play
```

***The donut code***

**NOTE: In all examples below the "$" is used to show the command prompt and should not be typed in when you copy the command.**


We'll use this fun code to learn how to compile and run a C code. 

*About the code:* 

This code uses ASCII characters (those on your keyboard) as pixels. 

To generally understand what it is doing, think of the 3-D shape of a donut, now imagine drawing just the part you see facing you in 2-D on a flat sheet of paper. The mathematical terminology for that 2-D drawing process is "making a 2-D projection of a 3-D object". The program uses geometry to project a 3-D donut onto the 2-D plane of your screen and it renders that projection in ASCII characters. It then rotates the donut and does the project again. It repeats this process until the user types "c" while holding "control" down to stop the program execution. The calculation and rendering of the projection and the rotation are handled by `for loops`.

```
#include <stdio.h>
#include <string.h>
int k;
double sin() ,cos();
main(){
    float A=0, B=0, i, j, z[1760];
    char b[1760];
    printf("\x1b[2J");
    for(; ; ) {
        memset(b,32,1760);
        memset(z,0,7040);
        for(j=0; 6.28>j; j+=0.03) {
            for(i=0; 6.28 >i; i+=0.01) {
                float sini=sin(i),
                      cosj=cos(j),
                      sinA=sin(A),
                      sinj=sin(j),
                      cosA=cos(A),
                      cosj2=cosj+2,
                      mess=1/(sini*cosj2*sinA+sinj*cosA+5),
                      cosi=cos(i),
                      cosB=cos(B),
                      sinB=sin(B),
                      t=sini*cosj2*cosA-sinj* sinA;
                int x=40+30*mess*(cosi*cosj2*cosB-t*sinB),
                    y= 12+15*mess*(cosi*cosj2*sinB +t*cosB),
                    o=x+80*y,
                    N=8*((sinj*sinA-sini*cosj*cosA)*cosB-sini*cosj*sinA-sinj*cosA-cosi *cosj*sinB);
                if(22>y&&y>0&&x>0&&80>x&&mess>z[o]){
                    z[o]=mess;
                    b[o]=".,-~:;=!*#$@"[N>0?N:0];
                }
            }
        }
        printf("\x1b[d");
        for(k=0; 1761>k; k++)
            putchar(k%80?b[k]:10);
        A+=0.04;
        B+= 0.02;
    }
}
```
The donut.c code is included in this repo. 

We will use the GNU compiler to compile this code. The compiler translates the code into 
machine language that the computer can understand and writes an executable file for you to run. 
This initial translation of all of the code is what gives compiled languages their speed for HPC 
because no time is need for the computer to interpret the code as it runs. 

The compile command for the GNU compiler is `gcc`, Compile the code with:

```
$ gcc -o -lm donut donut.c
```
This generates a file that you can run (an executable) called `donut’. -o is compiler flag that allows you to name the executable. The -lm flags links the math library that contains the sin and cos functions needed for the program. Compiler flags are special instruction for the compiler that you wouldn't want to code into your program directly because which flags you need depend on the selected compiler.

To make sure the file is there, do:

```
$ ls
```

```
README.md	donut		donut.c		heart.c
```




To run the code:
```
$ ./donut
```
To stop the program, hold down the control key while pressing "c". 

***The Heart Code***

```

Enter the number of rows
9
  SSSS     SSSS
 SSSSSS   SSSSSS
SSSSSSSS SSSSSSSS
SSSSSSSSSSSSSSSSS
 SSSSSSSSSSSSSSS
  SSSSSSSSSSSSS
   SSSSSSSSSSS
    SSSSSSSSS
     SSSSSSS
      SSSSS
       SSS
        S
```

Below is a code written in C that draws a heart on the screen in ASCII characters. 
The user can control the size of the heart by entering the number of rows for the main body of the heart.
We are going to use this code to introduce you to C. 

**NOTE: In all examples below the "$" is used to show the command prompt and should not be typed in when you copy the command.**

`heart.c`

```
#include <stdio.h>

int main() {
    int i,j, rows;

    printf("Enter the number of rows\n");
    scanf("%d", &rows);
    /* printing top semi circular shapes of heart */
    for(i = rows/2; i <= rows; i+=2){
     /* Printing Spaces */
        for(j = 1; j < rows-i; j+=2) {
            printf(" ");
        }
        /* printing Ss for left semi circle */
        for(j = 1; j <= i; j++){
            printf("S");
        }
        /* Printing Spaces */
        for(j = 1; j <= rows-i; j++){
            printf(" ");
        }
        /* printing Ss for right semi circle */
        for(j = 1; j <= i; j++){
            printf("S");
        }
        /* move to next row */
        printf("\n");
    }

    /* printing inverted start pyramid */
    for(i = rows; i >= 1; i--){
        for(j = i; j < rows; j++){
            printf(" ");
        }
        for(j = 1; j <= (i*2)-1; j++){
            printf("S");
        }
        /* move to next row */
        printf("\n");
    }

    return 0;
}
```
 This code is also included in this repository in a file called heart.c. 

**Compile and Run the Code** 

We will use the GNU compiler to compile this code. The compiler translates the code into 
machine language that the computer can understand and writes an executable file for you to run. 
This initial translation of all of the code is what gives compiled languages their speed for HPC 
because no time is need for the computer to interpret the code as it runs. 

***Exercise 1***

The compile command for the GNU compiler is `gcc`, Compile the code with:

```
$ gcc heart.c 

```
This generates a file that you can run (an executable) called `a.out’. a.out is the default name for an executable generated by most compilers. 

To run the program: 

```
$ ./a.out

```

You should see a heart of the size you specified by giving the program the number of rows. 
Play with this code by running it with different numbers of rows. 

* What part of the heart has the number of rows you chose? 
* What character is the heart made of? 
* How tall are the top semi-circles the heart? 

**Put Your Initials in the Heart** 

***Exercise 2***

Now let’s modify the code by changing the printed characters to be your initial. 

First copy the original code to a new file called heart_mod.c

```
$ cp heart.c heart_mod.c

```
Then look at the file with vi. 

```
$ vi heart_mod.c 

```
To put vi in "Insert" mode type ‘i’. Your terminal screen should say -- INSERT --  in the bottom left corner. vi behaves a lot like any word processor when it is in Insert mode. You can move the cursor with the arrows and delete and add charters just like you would in MSWord, but you cannot move the cursor with your mouse. 

Look for all the places in the code that have ` printf("S");’.

Replace each of the three different “S”s with each of your initials. 

To save your changes. Type “:wq”.  This will close vi and save your changes. 

Recompile and run the code. 


**Change the Shape of the Heart**

Now let’s try changing the shape of the heart. We’ll do this as an experiment. 

Line 9 of the code is the first i-based loop used to generate the top part of the heart, 
```
for(i = rows/2; i <= rows; i+=2){
```

***Exercise 4***

What happens to the shape of the heart if we change `; i+=2` on the end of the loop to `; i+=3`?

Make this change and recompile and run the code. 
 
What happens to the shape of the heart if we change `; i+=3` on the end of the loop to `; i+=1`?

Make this change and recompile and run the code. 

So, what is going on? 


The heart is generated by code structures called `for loops`. Loops allow sections of code to be repeated a specified number of times. Each trip through the loop is called an iteration. The heart code is made of sets of loops that depend on one another. These loops change the values of variables i and j sequentially.  

Specifically, j controls calculating how many spaces and charters to print in each row, and i controls how many rows are printed and limits the maximum value of j per row. 

Let's look at the language of the loop we just experimented with from line 9.

 
```
for(i = rows/2; i <= rows; i+=2){

```
In English this says, 

`For`  for

`i-rows/2;`   i equal to the number of rows divided by 2,

`i <= rows;` as long as i is less than or equal to the number of rows,

`i+=2` increment i in steps of 2. 

`{  ` Do this loop with all the code contained in the brackets. 

So, if you have entered 6 for the number of rows, 
this loop will start at 3, (6/2), and then move to 5, (3+2), and then to 7, (5+2), but 7 is greater than the number of rows, (6), so the loop will stop running before it executes that third iteration. If you compile and run the original code, heart.c, you will see that if you pick 6 rows, the top half circles of the heart are only two rows tall. 

The `%d` is formatting that tells the program to print an integer. 

If you look back over the for loops of the heart code, you will see that there are a few different ways of incrementing loop variables. 

`i+=2` increase i by two at the beginning of each loop. 

`j++` increase j by 1 at the beginning of each loop. This could also be written as `j+=1`

`i--` decrease j by 1 at the beginning of each loop. 

***Explorations***

1. If you want to explore how the range of i values and height of the top if the heart change with the number of rows you choose, then copy your heart.c file to a heart_count.c file and add the following print statement just after line 9. 

```
printf("i %d",i);
```

2. If there is time left, play with all the `for loop` limits to change the shape of the heart. 




**References**

Exercises based on:
https://gist.github.com/gcr/1075131
https://www.techcrashcourse.com/2016/02/print-heart-star-pattern-in-c.html



