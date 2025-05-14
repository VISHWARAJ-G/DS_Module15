# Ex15 - Largest Element in BST

## DATE: 21-03-2025

---

## AIM:
To write a C program to find the largest value in a Binary Search Tree.

---

## Algorithm

1. Start from the root of the Binary Search Tree.  
2. Traverse to the right child repeatedly.  
3. The rightmost node in a BST is the node with the largest value.  
4. Return the value of this rightmost node.  
5. If the tree is empty, indicate that no largest element exists.

---

## Program:

```c
/*
Program to find the largest value in a Binary Search Tree
Developed by: Vishwaraj G.
RegisterNumber:  212223220125
*/

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Function to create a new node
struct Node* createNode(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->left = newNode->right = NULL;
    return newNode;
}

// Function to insert a node in BST
struct Node* insert(struct Node* root, int value) {
    if (root == NULL)
        return createNode(value);
    
    if (value < root->data)
        root->left = insert(root->left, value);
    else
        root->right = insert(root->right, value);
    
    return root;
}

// Function to find the largest value
int findLargest(struct Node* root) {
    if (root == NULL) {
        printf("The tree is empty.\n");
        return -1;
    }

    struct Node* current = root;
    while (current->right != NULL)
        current = current->right;
    
    return current->data;
}

int main() {
    struct Node* root = NULL;
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 70);
    insert(root, 20);
    insert(root, 40);
    insert(root, 60);
    insert(root, 90);

    printf("The largest element in the BST is: %d\n", findLargest(root));
    return 0;
}
```
## Output:
```
The largest element in the BST is: 90
```
## Result:
Thus, the C program to find the largest value in a Binary Search Tree is implemented successfully.
