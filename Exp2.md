# EXPERIMENT 2 — PASSING AND RETURNING STRUCTURES

## Aim
To write a C program for passing a structure as a function argument and returning a structure from a function.

## Algorithm
1. Define a structure `numbers` with members `a` and `b`.
2. Declare a variable `n` of type `numbers`.
3. Input values for `a` and `b`.
4. Pass `n` to the `add()` function.
5. Add the two values inside the function.
6. Return the resulting structure.
7. Print the result.

## Program
```c
#include <stdio.h>

struct numbers {
    int a;
    int b;
};

struct numbers add(struct numbers n) {
    n.a = n.a + n.b;
    return n;
}

int main(void) {
    struct numbers n, result;

    scanf("%d %d", &n.a, &n.b);
    result = add(n);

    printf("Sum = %d\n", result.a);
    return 0;
}
```

## Output
```text
10 20
Sum = 30
```

## Result
Thus, the program is verified successfully.
