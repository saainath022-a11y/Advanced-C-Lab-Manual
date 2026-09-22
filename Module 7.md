# ADVANCED C LAB — MODULE 7

---

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
    printf("Name: %s\nAge: %d\n", e.n, e.age);
    printf("Vaccine Eligibility: %s\n", e.age > 6 ? "Yes" : "No");
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

---

# EXPERIMENT 2 — PASSING STRUCTURES AS FUNCTION ARGUMENTS AND RETURNING A STRUCTURE

## Aim
To write a C program for passing a structure as a function argument and returning a structure from a function.

## Algorithm
1. Define structure `numbers` with members `a` and `b`.
2. Declare variable `n` of type `numbers`.
3. Input values for `a` and `b`.
4. Pass `n` to the `add()` function.
5. Add the two values inside the function.
6. Return the resulting structure.
7. Print the result.

## Program
```c
#include <stdio.h>

struct numbers {
    int a, b;
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

---

# EXPERIMENT 3 — READ A FILE NAME AND WRITE THAT FILE USING FOPEN()

## Aim
To write a C program to read a file name from the user.

## Algorithm
1. Include the necessary header file `stdio.h`.
2. Begin the `main()` function.
3. Declare a file pointer `p` and a character array `name` to store the file name.
4. Prompt the user to enter a file name and read it using `scanf()`.
5. Use `fopen()` to open the file in write mode.
6. Print an error message if `fopen()` fails; otherwise print that the file was opened.
7. Use `fclose()` to close the file.
8. Print a message indicating that the file has been closed.
9. Return 0.

## Program
```c
#include <stdio.h>

int main(void) {
    FILE *p;
    char name[100];

    scanf("%99s", name);
    p = fopen(name, "w");

    if (p == NULL) {
        printf("Unable to open file\n");
        return 1;
    }

    printf("%s Opened Successfully\n", name);
    fclose(p);
    printf("File Closed Successfully\n");
    return 0;
}
```

## Output
```text
data.txt
data.txt Opened Successfully
File Closed Successfully
```

## Result
Thus, the program is verified successfully.

---

# EXPERIMENT 4 — READ A FILE NAME, WRITE THE FILE, AND INSERT TEXT

## Aim
To write a C program to read a file and insert text in that file.

## Algorithm
1. Include `stdio.h`.
2. Declare a file pointer, file name, text buffer, and number of strings.
3. Read the file name and number of strings.
4. Open the file in write mode.
5. Read each string and write it using `fputs()`.
6. Close the file and report success.
7. Return 0.

## Program
```c
#include <stdio.h>

int main(void) {
    FILE *p;
    char name[100], text[200];
    int num, i;

    printf("Enter file name: ");
    scanf("%99s", name);
    printf("Enter number of strings: ");
    scanf("%d", &num);

    p = fopen(name, "w");
    if (p == NULL) {
        printf("Unable to open file\n");
        return 1;
    }

    getchar();
    for (i = 0; i < num; i++) {
        fgets(text, sizeof(text), stdin);
        fputs(text, p);
    }

    fclose(p);
    printf("Data added successfully\n");
    return 0;
}
```

## Output
```text
Enter file name: notes.txt
Enter number of strings: 2
C programming
File handling
Data added successfully
```

## Result
Thus, the program is verified successfully.

---

# EXPERIMENT 5 — DISPLAY STUDENT DETAILS USING STRUCTURE

## Aim
To dynamically allocate memory to store information about multiple subjects, input the details, display the stored information, and free the allocated memory.

## Algorithm
1. Input the number of subjects.
2. Read `n` from the user.
3. Dynamically allocate memory for `n` subject structures.
4. If allocation fails, display an error and terminate.
5. Read each subject name and marks.
6. Display all subject details.
7. Free the allocated memory.
8. Return 0.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Subject {
    char name[50];
    int marks;
};

int main(void) {
    int n, i;
    struct Subject *s;

    printf("Enter number of subjects: ");
    scanf("%d", &n);

    s = malloc(n * sizeof(struct Subject));
    if (s == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }

    for (i = 0; i < n; i++) {
        printf("Enter subject name and marks: ");
        scanf("%49s %d", s[i].name, &s[i].marks);
    }

    printf("\n--- Subject Details ---\n");
    for (i = 0; i < n; i++)
        printf("%s : %d\n", s[i].name, s[i].marks);

    free(s);
    return 0;
}
```

## Output
```text
Enter number of subjects: 3
Enter subject name and marks: C 85
Enter subject name and marks: Maths 90
Enter subject name and marks: Physics 88

--- Subject Details ---
C : 85
Maths : 90
Physics : 88
```

## Result
Thus, the program is verified successfully.
