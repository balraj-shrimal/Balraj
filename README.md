Stack Using SLL

#include <stdio.h>
#include <stdlib.h>

// Node structure
struct Node {
    int data;
    struct Node* next;
};

// Global pointer to the top of the stack
struct Node* top = NULL;

// Push operation
void push() {
    int value;
    printf("Enter value to push: ");
    scanf("%d", &value);

   struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    if (newNode == NULL) {
        printf("Memory allocation failed\n");
        return;
    }

  newNode->data = value;
    newNode->next = top;
    top = newNode;

   printf("Pushed %d onto the stack.\n", value);
}

// Pop operation
void pop() {
    if (top == NULL) {
        printf("Stack underflow. No elements to pop.\n");
        return;
    }

   struct Node* temp = top;
    int poppedData = temp->data;
    top = top->next;
    free(temp);

  printf("Popped value: %d\n", poppedData);
}

// Peek operation
void peek() {
    if (top == NULL) {
        printf("Stack is empty.\n");
        return;
    }
    printf("Top value: %d\n", top->data);
}

// Display stack
void display() {
    if (top == NULL) {
        printf("Stack is empty.\n");
        return;
    }

  struct Node* temp = top;
    printf("Stack elements: ");
    while (temp != NULL) {
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

// Main function
int main() {
    int choice;

  do {
        printf("\n--- Stack Menu ---\n");
        printf("1. Push\n");
        printf("2. Pop\n");
        printf("3. Peek\n");
        printf("4. Display\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

  switch (choice) {
            case 1:
                push();
                break;
            case 2:
                pop();
                break;
            case 3:
                peek();
                break;
            case 4:
                display();
                break;
            case 5:
                printf("Exiting program.\n");
                break;
            default:
                printf("Invalid choice! Please try again.\n");
        }
    } while (choice != 5);

  return 0;
}
