Below is a code written in C that draws a heart on the screen in ASCII charaters. 
The user is able to control the size of the heart by entering the nubmer of rows tall for the main body of the heart.
We are going to use this code to introduce you to C. 

Goals
* Learn to compile and run a C-code.
* Learn aboout a few of the basic coding structures in C.
* Play with the code to see what it does.

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
        /* printing stars for left semi circle */
        for(j = 1; j <= i; j++){
            printf("S");
        }
        /* Printing Spaces */
        for(j = 1; j <= rows-i; j++){
            printf(" ");
        }
        /* printing stars for right semi circle */
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


**Compile and Run the Code** 

Login to the open DTN and clone this repositry in your home area if you have not already done so. 

Login help: See slide 10 : https://docs.google.com/presentation/d/1xUCsLPY6ehkugdraxgoWCLAmrkWOod6IT0S07BYeDIg/edit?usp=sharing

To clone: 

```
git clone 

```

We will use some Unix commands to change to the directory where the code is. 


