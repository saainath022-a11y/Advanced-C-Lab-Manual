# ADVANCED C LAB — MODULE 10

---

# EXPERIMENT 16 — SEARCH A GIVEN ELEMENT IN A LINKED LIST

## Aim
To write a C program to search a given element in a linked list.

## Algorithm
1. Define the structure for a node.
2. Create the linked list.
3. Read the element to be searched.
4. Traverse the list and compare each node's data with the key.
5. Report the position if found; otherwise report not found.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

void search(struct Node *head, int key) {
    int position = 1;

    while (head != NULL) {
        if (head->data == key) {
            printf("Element %d found at position %d\n", key, position);
            return;
        }
        head = head->next;
        position++;
    }

    printf("Element %d not found\n", key);
}

int main(void) {
    struct Node *head = NULL, *tail = NULL, *p;
    int n, i, value, key;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        p = malloc(sizeof(struct Node));
        if (p == NULL) return 1;
        p->data = value;
        p->next = NULL;

        if (head == NULL)
            head = tail = p;
        else {
            tail->next = p;
            tail = p;
        }
    }

    scanf("%d", &key);
    search(head, key);

    while (head != NULL) {
        p = head;
        head = head->next;
        free(p);
    }

    return 0;
}
```

## Output
```text
5
10 20 30 40 50
30
Element 30 found at position 3
```

## Result
Thus, the program to search a given element in the linked list is verified successfully.

---

# EXPERIMENT 17 — INSERT A NODE IN A LINKED LIST

## Aim
To write a C program to insert a node in a linked list.

## Algorithm
1. Define the structure for a node in a linked list.
2. Define the `insert()` function to insert a new node at the end.
3. Initialize `head` as `NULL`.
4. Read data and call `insert()` for each node.
5. Display the linked list.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

void insert(struct Node **head, int value) {
    struct Node *p = malloc(sizeof(struct Node));
    if (p == NULL) return;

    p->data = value;
    p->next = NULL;

    if (*head == NULL) {
        *head = p;
        return;
    }

    struct Node *temp = *head;
    while (temp->next != NULL)
        temp = temp->next;
    temp->next = p;
}

int main(void) {
    struct Node *head = NULL, *temp;
    int n, i, value;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        insert(&head, value);
    }

    printf("Linked list: ");
    temp = head;
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");

    while (head != NULL) {
        temp = head;
        head = head->next;
        free(temp);
    }

    return 0;
}
```

## Output
```text
3
10 20 30
Linked list: 10 20 30
```

## Result
Thus, the program to insert a node in a linked list is verified successfully.

---

# EXPERIMENT 18 — TRAVERSE A DOUBLY LINKED LIST

## Aim
To write a C program to traverse a doubly linked list.

## Algorithm
1. Create a doubly linked list.
2. Initialize `temp` to `head`.
3. Traverse while `temp != NULL`.
4. Print the data and move `temp` to `temp->next`.
5. End.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *prev, *next;
};

int main(void) {
    struct Node *head = NULL, *tail = NULL, *p;
    int n, i, value;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        p = malloc(sizeof(struct Node));
        if (p == NULL) return 1;

        p->data = value;
        p->prev = tail;
        p->next = NULL;

        if (tail != NULL)
            tail->next = p;
        else
            head = p;

        tail = p;
    }

    printf("Doubly linked list: ");
    for (p = head; p != NULL; p = p->next)
        printf("%d ", p->data);
    printf("\n");

    while (head != NULL) {
        p = head;
        head = head->next;
        free(p);
    }

    return 0;
}
```

## Output
```text
3
10 20 30
Doubly linked list: 10 20 30
```

## Result
Thus, the program to traverse a doubly linked list is verified successfully.

---

# EXPERIMENT 19 — INSERT AN ELEMENT IN A DOUBLY LINKED LIST

## Aim
To write a C program to insert an element in a doubly linked list.

## Algorithm
1. Create a new node and allocate memory.
2. Set its data.
3. If the list is empty, make it the head.
4. Otherwise traverse to the last node.
5. Connect the new node using `prev` and `next` pointers.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *prev, *next;
};

void insertEnd(struct Node **head, int value) {
    struct Node *newNode = malloc(sizeof(struct Node));
    if (newNode == NULL) return;

    newNode->data = value;
    newNode->next = NULL;
    newNode->prev = NULL;

    if (*head == NULL) {
        *head = newNode;
        return;
    }

    struct Node *temp = *head;
    while (temp->next != NULL)
        temp = temp->next;

    temp->next = newNode;
    newNode->prev = temp;
}

int main(void) {
    struct Node *head = NULL, *temp;
    int n, i, value;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        insertEnd(&head, value);
    }

    printf("List after insertion: ");
    for (temp = head; temp != NULL; temp = temp->next)
        printf("%d ", temp->data);
    printf("\n");

    while (head != NULL) {
        temp = head;
        head = head->next;
        free(temp);
    }

    return 0;
}
```

## Output
```text
3
10 20 30
List after insertion: 10 20 30
```

## Result
Thus, the program to insert an element in a doubly linked list is verified successfully.

---

# EXPERIMENT 20 — DELETE A GIVEN ELEMENT FROM A LINKED LIST

## Aim
To write a C function that deletes a given element from a linked list.

## Algorithm
1. Check whether the list is empty.
2. Traverse the list to find the element.
3. If the element is in the first node, update `head` and free the node.
4. Otherwise link the previous node to the next node and free the target node.
5. Report if the element is not found.

## Program
```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

void deleteElement(struct Node **head, int key) {
    struct Node *current = *head;
    struct Node *previous = NULL;

    while (current != NULL && current->data != key) {
        previous = current;
        current = current->next;
    }

    if (current == NULL) {
        printf("Element %d not found\n", key);
        return;
    }

    if (previous == NULL)
        *head = current->next;
    else
        previous->next = current->next;

    free(current);
    printf("Element %d deleted\n", key);
}

int main(void) {
    struct Node *head = NULL, *tail = NULL, *p;
    int n, i, value, key;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &value);
        p = malloc(sizeof(struct Node));
        if (p == NULL) return 1;

        p->data = value;
        p->next = NULL;

        if (head == NULL)
            head = tail = p;
        else {
            tail->next = p;
            tail = p;
        }
    }

    scanf("%d", &key);
    deleteElement(&head, key);

    printf("List: ");
    for (p = head; p != NULL; p = p->next)
        printf("%d ", p->data);
    printf("\n");

    while (head != NULL) {
        p = head;
        head = head->next;
        free(p);
    }

    return 0;
}
```

## Output
```text
5
10 20 30 40 50
30
Element 30 deleted
List: 10 20 40 50
```

## Result
Thus, the function that deletes a given element from a linked list is verified successfully.
