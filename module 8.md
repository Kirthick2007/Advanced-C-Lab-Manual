EXP NO:6 C PROGRAM PRINT THE LOWERCASE ENGLISH WORD CORRESPONDING TO THE NUMBER
Aim:
To write a C program print the lowercase English word corresponding to the number
Algorithm:
1.	Start
- Initialize an integer variable n.
2.	Input Validation
3.	Switch Statement cases.
-	Case 5: Print "seventy one"
-	Case 6: Print "seventy two"
-	Case 13: Print "seventy three"
-	...
-	Case 13: Print "seventy nine"
-	Default: Print "Greater than 13"
4.	Exit the program.
 
Program:
```
#include <stdio.h>

int main() {
    int n;

  
    printf("Enter a number: ");
    scanf("%d", &n);

    
    switch(n) {
        case 5:  printf("five\n"); break;
        case 6:  printf("six\n"); break;
        case 7:  printf("seven\n"); break;
        case 8:  printf("eight\n"); break;
        case 9:  printf("nine\n"); break;
        case 10: printf("ten\n"); break;
        case 11: printf("eleven\n"); break;
        case 12: printf("twelve\n"); break;
        case 13: printf("thirteen\n"); break;

        default:
            printf("Greater than 13\n");
    }

    return 0;
}

```

Output:
<img width="267" height="130" alt="image" src="https://github.com/user-attachments/assets/01b5e0a4-a762-420e-a4d8-4bbf41180535" />





Result:
Thus, the program is verified successfully
 
EXP NO:7 C PROGRAM TO PRINT TEN SPACE-SEPARATED INTEGERS     IN A SINGLE  LINE DENOTING THE FREQUENCY OF EACH DIGIT FROM 0 TO 3 .
Aim:
To write a C program to print ten space-separated integers in a single line denoting the frequency of each digit from 0 to 3.
Algorithm:
1.	Start
2.	Declare char array a[50] outer loop for each digit from 0 to 3
3.	Initialize counter c to 0
4.	For each character in the string print count c for current digit, followed by a space
5.	Increment h to move to the next digit
6.	End
 
Program:
```
#include <stdio.h>
#include <string.h>

int main() {
    char a[50];
    int i, d, c;

    printf("Enter a string containing digits: ");
    scanf("%s", a);

    for (d = 0; d <= 3; d++) {
        c = 0; // Reset counter for each digit

        // Count occurrences of digit d
        for (i = 0; i < strlen(a); i++) {
            if (a[i] == (d + '0')) {
                c++;
            }
        }

        printf("%d ", c);
    }

    return 0;
}

```

Output:

<img width="485" height="147" alt="image" src="https://github.com/user-attachments/assets/91f0275b-0eaf-4e8c-ba4a-e17729392f8c" />





Result:
Thus, the program is verified successfully

EXP NO:8 C PROGRAM TO PRINT ALL OF ITS PERMUTATIONS IN STRICT LEXICOGRAPHICAL ORDER.
Aim:
To write a C program to print all of its permutations in strict lexicographical order.

Algorithm:
1.	Start
2.	Declare variables s (pointer to an array of strings) and n (number of strings)

3.	Memory Allocation
Dynamically allocate memory for s to store an array of strings
4.	Input
Read the number of strings n from the user Dynamically allocate memory for each string in s
5.	Permutation Generation Loop
6.	Memory Deallocation
Free the memory allocated for each string in s Free the memory allocated for s
7.	End
 
Program:
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void swap(char *a, char *b) {
    char temp = *a;
    *a = *b;
    *b = temp;
}

void permute(char *str, int l, int r) {
    if (l == r) {
        printf("%s\n", str);
        return;
    }

    for (int i = l; i <= r; i++) {
        swap((str + l), (str + i));
        permute(str, l + 1, r);
        swap((str + l), (str + i));  // backtrack
    }
}

int main() {
    char **s;
    int n;

    printf("Enter number of strings: ");
    scanf("%d", &n);

    s = (char **)malloc(n * sizeof(char *));
    if (s == NULL) {
        printf("Memory allocation failed!\n");
        return 1;
    }

    for (int i = 0; i < n; i++) {
        s[i] = (char *)malloc(50 * sizeof(char));
        if (s[i] == NULL) {
            printf("Memory allocation failed!\n");
            return 1;
        }

        printf("Enter string %d: ", i + 1);
        scanf("%s", s[i]);

        // Sort string for lexicographical starting point
        int len = strlen(s[i]);
        for (int a = 0; a < len - 1; a++)
            for (int b = a + 1; b < len; b++)
                if (s[i][a] > s[i][b])
                    swap(&s[i][a], &s[i][b]);

        printf("Permutations of %s:\n", s[i]);
        permute(s[i], 0, strlen(s[i]) - 1);
    }

    for (int i = 0; i < n; i++)
        free(s[i]);

    free(s);

```

Output:
<img width="597" height="752" alt="image" src="https://github.com/user-attachments/assets/954282b8-c93d-4a2a-9ad0-406e804be441" />



Result:
Thus, the program is verified successfully
 
EXP NO:9 C PROGRAM PRINT A PATTERN OF NUMBERS FROM 1 TO N AS
SHOWN BELOW.
Aim:
To write a C program to print a pattern of numbers from 1 to n as shown below.
Algorithm:
1.	Start
2.	Declare integer variables n, i, j, min
3.	Read the value of n from the user
4.	Calculate the length of the side of the square matrix: len = n * 2 - 1
5.	Matrix Generation Loop
6.	Calculate min as the minimum distance to the borders
7.	End
 
Program:

```
#include <stdio.h>

int main() {
    int n, i, j, min;
    
    // Step 3: Read n
    printf("Enter n: ");
    scanf("%d", &n);

    // Step 4: Calculate length of the square matrix
    int len = n * 2 - 1;

    // Step 5: Generate pattern
    for (i = 0; i < len; i++) {
        for (j = 0; j < len; j++) {

            // Step 6: Minimum distance to any border
            int top = i;
            int left = j;
            int right = (len - 1) - j;
            int bottom = (len - 1) - i;

            min = top;
            if (left < min) min = left;
            if (right < min) min = right;
            if (bottom < min) min = bottom;

            printf("%d ", n - min);
        }
        printf("\n");
    }

    return 0;
}

```



Output:

<img width="574" height="233" alt="image" src="https://github.com/user-attachments/assets/e39ecff1-d173-4874-a985-fdf14cabdb93" />







Result:
Thus, the program is verified successfully

EXP NO:10 C PROGRAM TO FIND A SQUARE  OF NUMBER USING FUNCTION WITHOUT ARGUMENTS WITH RETURN TYPE

Aim:

To write a C program that calculates the square of a number using a function that does not take any arguments, but returns the square of the number.

Algorithm:

1.	Start.
2.	Define a function square() with no parameters. This function will return an integer value.
3.	Inside the function:
o	Declare an integer variable to store the number.
o	Ask the user to input a number.
o	Calculate the square of the number (multiply the number by itself).
o	Return the squared value.
4.	In the main function:
o	Call the square() function and display the result.
5.	End.

Program:
```
#include <stdio.h>

// Step 2: Function without arguments but with return type
int square() {
    int n;

    // Ask user for a number
    printf("Enter a number: ");
    scanf("%d", &n);

    // Step 3: Return the square
    return n * n;
}

int main() {
    int result;

    // Step 4: Call the function
    result = square();

    // Display the result
    printf("Square = %d\n", result);

    return 0;   // Step 5: End
}

```
Output:
<img width="226" height="142" alt="image" src="https://github.com/user-attachments/assets/bdf18fff-fb7d-4cff-9f37-54f236e0d38d" />




Result:
Thus, the program is verified successfully



























