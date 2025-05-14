# Ex13 - Expression Tree

## DATE: 19-03-2025

---

## AIM:
To write a C function to construct an Expression Tree for the given Postfix Expression and display the output in the format of In-order, Pre-order, and Post-order traversal.

---

## Algorithm

1. Read the postfix expression from left to right.  
2. Create a stack to store tree nodes.  
3. For each character in the postfix expression:  
   - If it is an operand, create a new node and push it onto the stack.  
   - If it is an operator, pop two nodes from the stack, create a new node with the operator, and set the two popped nodes as its children. Push the new node back to the stack.  
4. After the entire postfix expression is scanned, the node remaining in the stack is the root of the expression tree.  
5. Perform In-order, Pre-order, and Post-order traversals from the root and display the expressions.

---

## Program:

```c
/*
Program to construct an Expression Tree for the given Postfix Expression and display the output in the format of In-order ,Pre-order and Post-order traversal.
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

struct Node {
    char data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(char value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->left = newNode->right = NULL;
    return newNode;
}

struct Node* stack[50];
int top = -1;

void push(struct Node* node) {
    stack[++top] = node;
}

struct Node* pop() {
    return stack[top--];
}

void inorder(struct Node* root) {
    if (root) {
        if (root->left) printf("(");
        inorder(root->left);
        printf("%c", root->data);
        inorder(root->right);
        if (root->right) printf(")");
    }
}

void preorder(struct Node* root) {
    if (root) {
        printf("%c", root->data);
        preorder(root->left);
        preorder(root->right);
    }
}

void postorder(struct Node* root) {
    if (root) {
        postorder(root->left);
        postorder(root->right);
        printf("%c", root->data);
    }
}

int main() {
    char postfix[50];
    printf("Enter postfix expression: ");
    scanf("%s", postfix);

    for (int i = 0; postfix[i] != '\0'; i++) {
        char ch = postfix[i];
        struct Node* node = createNode(ch);

        if (isalnum(ch)) {
            push(node);
        } else {
            node->right = pop();
            node->left = pop();
            push(node);
        }
    }

    struct Node* root = pop();

    printf("Inorder   : ");
    inorder(root);
    printf("\n");

    printf("Preorder  : ");
    preorder(root);
    printf("\n");

    printf("Postorder : ");
    postorder(root);
    printf("\n");

    return 0;
}
```
## Output:
```
Enter postfix expression: ab+cde+**
Inorder   : ((a+b)*(c*(d+e)))
Preorder  : *+ab*c+de
Postorder : ab+cde+* *
```
## Result:
Thus, the C program to construct an Expression Tree from a given postfix expression and display the output in In-order, Pre-order, and Post-order traversals is implemented successfully.
