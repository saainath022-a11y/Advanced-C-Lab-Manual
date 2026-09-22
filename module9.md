# ADVANCED C LAB — MODULE 9

---

# EXPERIMENT 11 — DISPLAY STACK ELEMENTS USING AN ARRAY

## Aim
To write a C program to display stack elements using an array.

## Algorithm
1. Declare a stack array and `top`.
2. Initialize `top` to `-1`.
3. Read stack elements using push operations.
4. Traverse from `top` to 0 and display each element.
5. End.

## Program
```c
#include <stdio.h>
#define MAX 5

int main(void) {
    int stack[MAX], top = -1, n, i;

    printf("Enter number of elements: ");
    scanf("%d", &n);
    if (n > MAX) n = MAX;

    for (i = 0; i < n; i++)
        scanf("%d", &stack[++top]);

    printf("Stack elements: ");
    for (i = top; i >= 0; i--)
        printf("%d ", stack[i]);
    printf("\n");

    return 0;
}
```

## Output
```text
Enter number of elements: 3
10 20 30
Stack elements: 30 20 10
```

## Result
Thus, the program to display stack elements using an array is verified successfully.

---

# EXPERIMENT 12 — PUSH AN ELEMENT INTO A STACK USING ARRAY

## Aim
To create a C program to push the given element into a stack using an array.

## Algorithm
1. Declare the stack size, `top` index, and stack array.
2. Initialize `top` to `-1`.
3. Read the element.
4. Check for stack overflow.
5. Increment `top` and store the element.
6. Display the stack top.

## Program
```c
#include <stdio.h>
#define MAX 5

int stack[MAX], top = -1;

void push(int value) {
    if (top == MAX - 1) {
        printf("Stack Overflow\n");
        return;
    }
    stack[++top] = value;
    printf("%d pushed into stack\n", value);
}

int main(void) {
    int value;

    printf("Enter element: ");
    scanf("%d", &value);
    push(value);
    printf("Stack top = %d\n", stack[top]);

    return 0;
}
```

## Output
```text
Enter element: 50
50 pushed into stack
Stack top = 50
```

## Result
Thus, the program to push the given element into a stack using an array is verified successfully.

---

# EXPERIMENT 13 — DISPLAY QUEUE ELEMENTS USING ARRAY

## Aim
To write a C program to display queue elements using an array.

## Algorithm
1. Declare queue, `front`, and `rear`.
2. Initialize `front = 0` and `rear = -1`.
3. Read queue elements.
4. Traverse from `front` to `rear` and display them.
5. End.

## Program
```c
#include <stdio.h>
#define MAX 5

int main(void) {
    int queue[MAX], front = 0, rear = -1, n, i;

    printf("Enter number of elements: ");
    scanf("%d", &n);
    if (n > MAX) n = MAX;

    for (i = 0; i < n; i++)
        scanf("%d", &queue[++rear]);

    printf("Queue elements: ");
    for (i = front; i <= rear; i++)
        printf("%d ", queue[i]);
    printf("\n");

    return 0;
}
```

## Output
```text
Enter number of elements: 3
10 20 30
Queue elements: 10 20 30
```

## Result
Thus, the program to display queue elements using an array is verified successfully.

---

# EXPERIMENT 14 — INSERT ELEMENTS IN QUEUE USING ARRAY

## Aim
To write a C program to insert elements in a queue using an array.

## Algorithm
1. Declare queue size, `rear`, `front`, and the queue array.
2. Initialize `front = 0` and `rear = -1`.
3. Define `enqueue()` to check overflow and insert an element at `rear`.
4. Read elements and call `enqueue()`.
5. Display the queue.

## Program
```c
#include <stdio.h>
#define MAX 5

int queue[MAX], front = 0, rear = -1;

void enqueue(int value) {
    if (rear == MAX - 1) {
        printf("Queue Overflow\n");
        return;
    }
    queue[++rear] = value;
}

int main(void) {
    int n, value, i;

    printf("Enter number of elements: ");
    scanf("%d", &n);
    if (n > MAX) n = MAX;

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        enqueue(value);
    }

    printf("Queue: ");
    for (i = front; i <= rear; i++)
        printf("%d ", queue[i]);
    printf("\n");

    return 0;
}
```

## Output
```text
Enter number of elements: 3
10 20 30
Queue: 10 20 30
```

## Result
Thus, the program to insert elements in a queue using an array is verified successfully.

---

# EXPERIMENT 15 — DELETE ELEMENTS IN QUEUE USING ARRAY

## Aim
To create a C function that deletes an element from a queue implemented using an array.

## Algorithm
1. Check if the queue is empty.
2. If `front == -1`, report an empty queue.
3. Otherwise, delete the front element and increment `front`.
4. If `front` becomes greater than `rear`, reset both to `-1`.
5. End the function.

## Program
```c
#include <stdio.h>
#define MAX 5

int queue[MAX] = {10, 20, 30, 40, 50};
int front = 0, rear = 4;

void dequeue(void) {
    if (front == -1) {
        printf("Queue is empty\n");
        return;
    }

    printf("Deleted element: %d\n", queue[front++]);
    if (front > rear)
        front = rear = -1;
}

int main(void) {
    printf("Initial queue: 10 20 30 40 50\n");
    dequeue();

    printf("Queue after deletion: ");
    if (front == -1) {
        printf("empty\n");
    } else {
        for (int i = front; i <= rear; i++)
            printf("%d ", queue[i]);
        printf("\n");
    }

    return 0;
}
```

## Output
```text
Initial queue: 10 20 30 40 50
Deleted element: 10
Queue after deletion: 20 30 40 50
```

## Result
Thus, the function that deletes an element from a queue implemented using an array is verified successfully.
