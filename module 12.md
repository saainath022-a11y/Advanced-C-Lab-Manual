# ADVANCED C LAB — MODULE 12

---

# EXPERIMENT 26 — DISPLAY STACK ELEMENTS USING LINKED LIST

## Aim
To write a C program to display stack elements using a linked list.

## Algorithm
1. Define a `Node` with `data` and `next`.
2. Maintain `top` as the head of the stack.
3. Push the input elements onto the stack.
4. Traverse from `top` to `NULL` and print each element.
5. End.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

int main(void) {
    struct Node *top = NULL, *p;
    int n, i, value;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        p = malloc(sizeof(struct Node));
        if (p == NULL) return 1;

        p->data = value;
        p->next = top;
        top = p;
    }

    printf("Stack elements: ");
    for (p = top; p != NULL; p = p->next)
        printf("%d ", p->data);
    printf("\n");

    while (top != NULL) {
        p = top;
        top = top->next;
        free(p);
    }

    return 0;
}
```

## Output
```text
3
10 20 30
Stack elements: 30 20 10
```

## Result
Thus, the program to display stack elements using a linked list is verified successfully.

---

# EXPERIMENT 27 — POP AN ELEMENT FROM A STACK USING LINKED LIST

## Aim
To write a C program to pop an element from the given stack using a linked list.

## Algorithm
1. Check whether `top` is `NULL`.
2. If `top` is `NULL`, print **Stack is empty**.
3. Otherwise store `top` in a temporary pointer.
4. Move `top` to the next node.
5. Print and free the removed node.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

int main(void) {
    struct Node *top = NULL, *p;
    int n, i, value;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        p = malloc(sizeof(struct Node));
        if (p == NULL) return 1;

        p->data = value;
        p->next = top;
        top = p;
    }

    if (top == NULL) {
        printf("Stack is empty.\n");
    } else {
        p = top;
        printf("Popped element: %d\n", p->data);
        top = top->next;
        free(p);
    }

    while (top != NULL) {
        p = top;
        top = top->next;
        free(p);
    }

    return 0;
}
```

## Output
```text
3
10 20 30
Popped element: 30
```

## Result
Thus, the program to pop an element from the given stack using a linked list is verified successfully.

---

# EXPERIMENT 28 — DISPLAY QUEUE ELEMENTS USING LINKED LIST

## Aim
To write a C program to display queue elements using a linked list.

## Algorithm
1. Maintain `front` and `rear` pointers.
2. Insert elements into the queue.
3. Traverse from `front` while the pointer is not `NULL`.
4. Print each element.
5. End the display operation.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

int main(void) {
    struct Node *front = NULL, *rear = NULL, *p, *temp;
    int n, i, value;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        p = malloc(sizeof(struct Node));
        if (p == NULL) return 1;

        p->data = value;
        p->next = NULL;

        if (rear == NULL)
            front = rear = p;
        else {
            rear->next = p;
            rear = p;
        }
    }

    printf("Queue elements: ");
    for (temp = front; temp != NULL; temp = temp->next)
        printf("%d ", temp->data);
    printf("\n");

    while (front != NULL) {
        temp = front;
        front = front->next;
        free(temp);
    }

    return 0;
}
```

## Output
```text
3
10 20 30
Queue elements: 10 20 30
```

## Result
Thus, the program to display queue elements using a linked list is verified successfully.

---

# EXPERIMENT 29 — INSERT ELEMENTS IN QUEUE USING LINKED LIST

## Aim
To write a C program to insert elements in a queue using a linked list.

## Algorithm
1. Allocate memory for a new node.
2. Set its data and next pointer.
3. If the queue is empty, set both `front` and `rear` to the new node.
4. Otherwise connect the new node after `rear` and update `rear`.
5. Display the queue.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

void enqueue(struct Node **front, struct Node **rear, int value) {
    struct Node *p = malloc(sizeof(struct Node));
    if (p == NULL) return;

    p->data = value;
    p->next = NULL;

    if (*rear == NULL) {
        *front = *rear = p;
    } else {
        (*rear)->next = p;
        *rear = p;
    }
}

int main(void) {
    struct Node *front = NULL, *rear = NULL, *temp;
    int n, i, value;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        enqueue(&front, &rear, value);
    }

    printf("Queue: ");
    for (temp = front; temp != NULL; temp = temp->next)
        printf("%d ", temp->data);
    printf("\n");

    while (front != NULL) {
        temp = front;
        front = front->next;
        free(temp);
    }

    return 0;
}
```

## Output
```text
3
10 20 30
Queue: 10 20 30
```

## Result
Thus, the program to insert elements in a queue using a linked list is verified successfully.

---

# EXPERIMENT 30 — FIND THE PEEK OF A QUEUE USING LINKED LIST

## Aim
To retrieve the peek (front element) of a queue implemented using a linked list.

## Algorithm
1. Check whether the queue is empty.
2. If `front` is `NULL`, print a message indicating that the queue is empty.
3. Otherwise return or print the data stored at `front`.
4. End.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

int peek(struct Node *front) {
    if (front == NULL)
        return -1;
    return front->data;
}

int main(void) {
    struct Node *front = NULL, *rear = NULL, *p, *temp;
    int n, i, value, result;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        p = malloc(sizeof(struct Node));
        if (p == NULL) return 1;

        p->data = value;
        p->next = NULL;

        if (rear == NULL)
            front = rear = p;
        else {
            rear->next = p;
            rear = p;
        }
    }

    result = peek(front);

    if (result == -1)
        printf("Queue is empty\n");
    else
        printf("Peek element: %d\n", result);

    while (front != NULL) {
        temp = front;
        front = front->next;
        free(temp);
    }

    return 0;
}
```

## Output
```text
3
10 20 30
Peek element: 10
```

## Result
Thus, the program to retrieve the peek (front element) of a queue implemented using a linked list is verified successfully.
