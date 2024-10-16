# Experiment 6: Pseudorandom Number Generation

## AIM:
To implement pseudorandom number generation using the standard library in C.



## DESIGN STEPS:

### Step 1:
Declare the necessary variables for storing the count of random numbers, minimum and maximum values, and the generated random number.

### Step 2:
Prompt the user for the number of random numbers to be generated (`count`), and ensure the input is a valid positive integer.

### Step 3:
Prompt the user to input the minimum (`min`) and maximum (`max`) values for the range. Validate that the maximum value is greater than the minimum.

### Step 4:
Use the `srand(time(NULL))` function to seed the random number generator based on the current time.

### Step 5:
For the specified `count`, generate random numbers using the formula:

**random_number=(rand()%(max−min+1))+min**

Print each generated random number.

### Step 6:
End the program.



## PROGRAM:

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() 
{
    int count, min, max;

    // Input number of random numbers to generate
    printf("Enter the number of random numbers to generate: ");
    while (scanf("%d", &count) != 1 || count <= 0) 
    {
        printf("Invalid input. Please enter a positive integer: ");
        while (getchar() != '\n'); // Clear invalid input
    }

    // Input minimum value
    printf("Enter the minimum value: ");
    scanf("%d", &min);

    // Input maximum value
    printf("Enter the maximum value: ");
    while (scanf("%d", &max) != 1 || max <= min) 
    {
        printf("Invalid input. Maximum must be greater than minimum. Please enter again: ");
        while (getchar() != '\n');  // Clear invalid input
    }

    // Seed the random number generator
    srand(time(NULL));

    // Generate and print random numbers
    printf("\nPseudorandom numbers between %d and %d:\n", min, max);
    for (int i = 0; i < count; i++) 
    {
        int random_number = (rand() % (max - min + 1)) + min;
        printf("%d\n", random_number);
    }

    return 0;
}
```



## OUTPUT:

```
Enter the number of random numbers to generate: 5
Enter the minimum value: 10
Enter the maximum value: 20

Pseudorandom numbers between 10 and 20:
15
17
11
20
13
```



## RESULT:
The implementation of pseudorandom number generation using the standard library was successful.
