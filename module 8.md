# ADVANCED C LAB — MODULE 8

---

# EXPERIMENT 6 — PRINT THE LOWERCASE ENGLISH WORD CORRESPONDING TO A NUMBER

## Aim
To write a C program to print the lowercase English word corresponding to a number.

## Algorithm
1. Start.
2. Initialize integer variable `n`.
3. Read `n` from the user.
4. Use `switch` cases to print the corresponding lowercase English word.
5. Print a message for values outside the supported range.
6. Exit.

## Program
```c
#include <stdio.h>

int main(void) {
    int n;
    scanf("%d", &n);

    switch (n) {
        case 1: printf("one"); break;
        case 2: printf("two"); break;
        case 3: printf("three"); break;
        case 4: printf("four"); break;
        case 5: printf("five"); break;
        case 6: printf("six"); break;
        case 7: printf("seven"); break;
        case 8: printf("eight"); break;
        case 9: printf("nine"); break;
        default: printf("Greater than 9");
    }
    printf("\n");
    return 0;
}
```

## Output
```text
7
seven
```

## Result
Thus, the program is verified successfully.

---

# EXPERIMENT 7 — PRINT THE FREQUENCY OF DIGITS FROM 0 TO 3

## Aim
To write a C program to print ten space-separated integers in a single line denoting the frequency of each digit from 0 to 3.

## Algorithm
1. Start.
2. Declare a character array to store the input line.
3. Read the input line.
4. For each digit from 0 to 3, count its occurrences.
5. Print the four frequencies separated by spaces.
6. End.

## Program
```c
#include <stdio.h>

int main(void) {
    char a[100];
    int count[4] = {0, 0, 0, 0};
    int i;

    fgets(a, sizeof(a), stdin);
    for (i = 0; a[i] != '\0'; i++) {
        if (a[i] >= '0' && a[i] <= '3')
            count[a[i] - '0']++;
    }

    printf("%d %d %d %d\n", count[0], count[1], count[2], count[3]);
    return 0;
}
```

## Output
```text
0123012301
3 3 2 2
```

## Result
Thus, the program is verified successfully.

---

# EXPERIMENT 8 — PRINT ALL PERMUTATIONS IN STRICT LEXICOGRAPHICAL ORDER

## Aim
To write a C program to print all permutations of a string in strict lexicographical order.

## Algorithm
1. Read a string.
2. Sort the characters in ascending order.
3. Print the current permutation.
4. Generate the next lexicographical permutation by finding the rightmost increasing pair, swapping, and reversing the suffix.
5. Repeat until there is no next permutation.
6. End the program.

## Program
```c
#include <stdio.h>
#include <string.h>

void sort(char s[]) {
    int i, j;
    char t;
    for (i = 0; s[i]; i++)
        for (j = i + 1; s[j]; j++)
            if (s[i] > s[j]) {
                t = s[i];
                s[i] = s[j];
                s[j] = t;
            }
}

int next_permutation(char s[], int n) {
    int i = n - 2, j;
    char t;

    while (i >= 0 && s[i] >= s[i + 1])
        i--;

    if (i < 0)
        return 0;

    j = n - 1;
    while (s[j] <= s[i])
        j--;

    t = s[i];
    s[i] = s[j];
    s[j] = t;

    for (j = n - 1, i = i + 1; i < j; i++, j--) {
        t = s[i];
        s[i] = s[j];
        s[j] = t;
    }

    return 1;
}

int main(void) {
    char s[100];
    int n;

    scanf("%99s", s);
    n = (int)strlen(s);
    sort(s);

    do {
        printf("%s\n", s);
    } while (next_permutation(s, n));

    return 0;
}
```

## Output
```text
abc
abc
acb
bac
bca
cab
cba
```

## Result
Thus, the program is verified successfully.

---

# EXPERIMENT 9 — PRINT A NUMBER PATTERN FROM 1 TO N

## Aim
To write a C program to print a pattern of numbers from 1 to `n` as shown in the required format.

## Algorithm
1. Start.
2. Declare integer variables `n`, `i`, `j`, and `min`.
3. Read `n`.
4. Calculate `len = n * 2 - 1`.
5. For each position in the square, calculate the minimum distance from the four borders.
6. Print `n - min` for each position.
7. End.

## Program
```c
#include <stdio.h>

int main(void) {
    int n, i, j, len, min;
    scanf("%d", &n);
    len = 2 * n - 1;

    for (i = 0; i < len; i++) {
        for (j = 0; j < len; j++) {
            min = i < j ? i : j;
            if (len - 1 - i < min)
                min = len - 1 - i;
            if (len - 1 - j < min)
                min = len - 1 - j;
            printf("%d ", n - min);
        }
        printf("\n");
    }
    return 0;
}
```

## Output
```text
4
4 4 4 4 4 4 4
4 3 3 3 3 3 4
4 3 2 2 2 3 4
4 3 2 1 2 3 4
4 3 2 2 2 3 4
4 3 3 3 3 3 4
4 4 4 4 4 4 4
```

## Result
Thus, the program is verified successfully.

---

# EXPERIMENT 10 — FIND THE SQUARE USING A FUNCTION WITHOUT ARGUMENTS WITH RETURN TYPE

## Aim
To write a C program that calculates the square of a number using a function that takes no arguments but returns the square of the number.

## Algorithm
1. Start.
2. Define `square()` with no parameters and an integer return type.
3. Read a number inside `square()`.
4. Calculate and return its square.
5. Call `square()` from `main()` and display the result.
6. End.

## Program
```c
#include <stdio.h>

int square(void) {
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);
    return n * n;
}

int main(void) {
    int result = square();
    printf("Square = %d\n", result);
    return 0;
}
```

## Output
```text
Enter a number: 8
Square = 64
```

## Result
Thus, the program is verified successfully.
