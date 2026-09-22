# EXPERIMENT 1 — ARRAY OF STRUCTURE TO CHECK VACCINE ELIGIBILITY

## Aim
To write a C program using an array of structures to check vaccine eligibility for a person whose age is above 6 years.

## Algorithm
1. Declare a structure `eligible` with `age` and `n` members.
2. Declare a variable `e` of type `eligible`.
3. Input the name and age using `scanf()`.
4. If `e.age <= 6`, print **Vaccine Eligibility: No**.
5. Otherwise, print **Vaccine Eligibility: Yes**.
6. Display the name and age.
7. Return 0.

## Program
```c
#include <stdio.h>

struct eligible {
    int age;
    char n[50];
};

int main(void) {
    struct eligible e;

    scanf("%49s %d", e.n, &e.age);

    printf("Name: %s\n", e.n);
    printf("Age: %d\n", e.age);

    if (e.age <= 6)
        printf("Vaccine Eligibility: No\n");
    else
        printf("Vaccine Eligibility: Yes\n");

    return 0;
}
```

## Output
```text
Ram 25
Name: Ram
Age: 25
Vaccine Eligibility: Yes
```

## Result
Thus, the program is verified successfully.
