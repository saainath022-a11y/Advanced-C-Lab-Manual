# ADVANCED C LAB — MODULE 11

---

# EXPERIMENT 21 — FIND THE GREATEST NUMBER USING A FUNCTION

## Aim
To write a C program to create a function to find the greatest number.

## Algorithm
1. Include `stdio.h`.
2. Define `max_of_four()` to compare four integers and return the greatest.
3. Read four integers.
4. Call `max_of_four()` and print the result.
5. End.

## Program
```c
#include <stdio.h>

int max_of_four(int a, int b, int c, int d) {
    int max = a;

    if (b > max) max = b;
    if (c > max) max = c;
    if (d > max) max = d;

    return max;
}

int main(void) {
    int n1, n2, n3, n4, greater;

    scanf("%d %d %d %d", &n1, &n2, &n3, &n4);
    greater = max_of_four(n1, n2, n3, n4);

    printf("Greatest number = %d\n", greater);
    return 0;
}
```

## Output
```text
10 25 17 8
Greatest number = 25
```

## Result
Thus, the program that creates a function to find the greatest number is verified successfully.

---

# EXPERIMENT 22 — MAXIMUM VALUES FOR AND, OR, AND XOR COMPARISONS

## Aim
To write a C program to print the maximum values for the AND, OR, and XOR comparisons.

## Algorithm
1. Define `calculate_the_max(n, k)`.
2. Initialize maximum values for `&`, `|`, and `^` to zero.
3. Use nested loops for pairs `i < j`, with `i` and `j` from 1 to `n`.
4. Update each maximum only when the operation value is less than `k`.
5. Read `n` and `k` and call the function.

## Program
```c
#include <stdio.h>

void calculate_the_max(int n, int k) {
    int a = 0, o = 0, x = 0;
    int i, j, value;

    for (i = 1; i <= n; i++) {
        for (j = i + 1; j <= n; j++) {
            value = i & j;
            if (value < k && value > a) a = value;

            value = i | j;
            if (value < k && value > o) o = value;

            value = i ^ j;
            if (value < k && value > x) x = value;
        }
    }

    printf("%d\n%d\n%d\n", a, o, x);
}

int main(void) {
    int n, k;

    scanf("%d %d", &n, &k);
    calculate_the_max(n, k);

    return 0;
}
```

## Output
```text
5 4
2
3
3
```

## Result
Thus, the program to print the maximum values for the AND, OR, and XOR comparisons is verified successfully.

---

# EXPERIMENT 23 — WRITE THE LOGIC FOR THE REQUESTS

## Aim
To write a C program to implement the logic for the given requests involving shelves and books.

## Algorithm
1. Read the number of shelves and queries.
2. Use a 2D array to store book page counts and an array for the number of books on each shelf.
3. For type 1, add a book with the given page count to a shelf.
4. For type 2, print the page count of the requested book.
5. For type 3, print the number of books on the requested shelf.
6. Process all queries.

## Program
```c
#include <stdio.h>

int main(void) {
    int noshel, noque;
    scanf("%d %d", &noshel, &noque);

    int shelarr[noshel][100];
    int nobookarr[noshel];
    int i;

    for (i = 0; i < noshel; i++)
        nobookarr[i] = 0;

    for (i = 0; i < noque; i++) {
        int type, x, y;
        scanf("%d %d", &type, &x);

        if (type == 1) {
            scanf("%d", &y);
            if (x >= 0 && x < noshel && nobookarr[x] < 100)
                shelarr[x][nobookarr[x]++] = y;
        } else if (type == 2) {
            scanf("%d", &y);
            if (x >= 0 && x < noshel && y >= 0 && y < nobookarr[x])
                printf("%d\n", shelarr[x][y]);
        } else if (type == 3) {
            if (x >= 0 && x < noshel)
                printf("%d\n", nobookarr[x]);
        }
    }

    return 0;
}
```

## Output
```text
5 5
1 0 15
1 0 20
3 0
2 0 1
3 1
2
20
0
```

## Result
Thus, the program to implement the logic for the requests is verified successfully.

---

# EXPERIMENT 24 — FIND THE SUM OF INTEGERS IN AN ARRAY

## Aim
To write a C program to print the sum of the integers in an array.

## Algorithm
1. Read `n`.
2. Declare an array of size `n`.
3. Initialize `sum = 0`.
4. Read each element and add it to `sum`.
5. Print `sum`.

## Program
```c
#include <stdio.h>

int main(void) {
    int n, i, sum = 0;
    scanf("%d", &n);

    int a[n];

    for (i = 0; i < n; i++) {
        scanf("%d", &a[i]);
        sum += a[i];
    }

    printf("Sum = %d\n", sum);
    return 0;
}
```

## Output
```text
5
10 20 30 40 50
Sum = 150
```

## Result
Thus, the program that prints the sum of the integers in the array is verified successfully.

---

# EXPERIMENT 25 — COUNT THE NUMBER OF WORDS IN A SENTENCE

## Aim
To write a C program that counts the number of words in a given sentence.

## Algorithm
1. Input the sentence using `fgets()`.
2. Initialize a word counter and a flag indicating whether the program is inside a word.
3. Traverse each character.
4. When a non-space character starts a word, increment the counter.
5. Reset the flag when whitespace is found.
6. Display the word count.

## Program
```c
#include <stdio.h>
#include <ctype.h>

int main(void) {
    char sentence[500];
    int words = 0, in_word = 0, i;

    fgets(sentence, sizeof(sentence), stdin);

    for (i = 0; sentence[i] != '\0'; i++) {
        if (isspace((unsigned char)sentence[i])) {
            in_word = 0;
        } else if (!in_word) {
            words++;
            in_word = 1;
        }
    }

    printf("Number of words = %d\n", words);
    return 0;
}
```

## Output
```text
C programming is easy
Number of words = 4
```

## Result
Thus, the program that counts the number of words in a given sentence is verified successfully.
