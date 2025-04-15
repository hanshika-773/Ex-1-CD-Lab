# Ex-1 IMPLEMENTATION-OF-SYMBOL-TABLE
# Register Number : 212223240046
# Date : 15-04-2025
# AIM :
## To write a C program to implement a symbol table.
# ALGORITHM
1.	Start the program.
2.	Get the input from the user with the terminating symbol ‘$’.
3.	Allocate memory for the variable by dynamic memory allocation function.
4.	If the next character of the symbol is an operator then only the memory is allocated.
5.	While reading, the input symbol and memory address are inserted into the symbol table.
6.	The steps are repeated till ‘$’ is reached.
7.	To reach a variable, enter the variable to be searched and the symbol table has been checked for the corresponding variable, the variable along with its address is displayed as a result.
8.	Stop the program. 
# PROGRAM
```
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

#define MAX_EXPRESSION_SIZE 100
#define MAX_SYMBOLS 15

int main() {
    int i = 0, x = 0, n;
    void *add[MAX_SYMBOLS];
    char b[MAX_EXPRESSION_SIZE], d[MAX_SYMBOLS], c, srch;
    int found = 0;

    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0';
    n = i - 1;

    printf("\nGiven Expression: %s\n", b);
    printf("\nSymbol Table\n");
    printf("Symbol\tAddress\t\tType\n");

    for (int j = 0; j <= n && x < MAX_SYMBOLS; j++) {
        c = b[j];
        if (isalpha((unsigned char)c)) {
            int alreadyExists = 0;
            for (int k = 0; k < x; k++) {
                if (d[k] == c) {
                    alreadyExists = 1;
                    break;
                }
            }
            if (!alreadyExists) {
                void *p = malloc(sizeof(char));
                add[x] = p;
                d[x] = c;
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
        }
    }

    while (getchar() != '\n'); // Clear input buffer

    printf("\nEnter the symbol to be searched: ");
    srch = getchar();

    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("\n✅ Symbol Found!\n");
            printf("%c @ address %p\n", srch, add[i]);
            found = 1;
            break;
        }
    }

    if (!found) {
        printf("\nSymbol Not Found!\n");
    }

    for (i = 0; i < x; i++) {
        free(add[i]);
    }

    // 🔽 Pause so the window doesn't close immediately
    printf("\nPress Enter to exit...");
    while (getchar() != '\n'); // Wait for Enter key
    getchar();

    return 0;
}
```
# OUTPUT
![Screenshot 2025-04-15 111209](https://github.com/user-attachments/assets/48a183ff-f90f-4a72-9abb-384d7f8aa9d1)

![Screenshot 2025-04-15 111236](https://github.com/user-attachments/assets/d11a705a-1979-46e5-a920-e00d792dca83)

# RESULT
### The program to implement a symbol table is executed and the output is verified.
