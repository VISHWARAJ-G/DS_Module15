# Ex12 - Binary Search Tree

## DATE: 18-03-2025

---

## AIM:
To write a C function to insert the elements in the binary search tree.

---

## Algorithm

1. Start with an empty binary search tree (BST).  
2. Create a new node with the given data.  
3. If the tree is empty, set the new node as the root.  
4. Else, compare the data to be inserted with the current node's data:  
   - If it is smaller, move to the left child.  
   - If it is greater, move to the right child.  
5. Repeat step 4 until the correct position is found and insert the new node.

---

## Program:

```c
/*
Program to insert the elements in the binary search tree
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* createNode(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->left = newNode->right = NULL;
    return newNode;
}

struct Node* insert(struct Node* root, int value) {
    if (root == NULL)
        return createNode(value);
    if (value < root->data)
        root->left = insert(root->left, value);
    else if (value > root->data)
        root->right = insert(root->right, value);
    return root;
}

void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}

int main() {
    struct Node* root = NULL;
    int values[] = {50, 30, 70, 20, 40, 60, 80};
    int n = sizeof(values) / sizeof(values[0]);

    for (int i = 0; i < n; i++)
        root = insert(root, values[i]);

    printf("Inorder Traversal of BST: ");
    inorder(root);
    printf("\n");

    return 0;
}
```
## Output:
```
Inorder Traversal of BST: 20 30 40 50 60 70 80
```
## Result:
Thus, the C function to insert the elements in the binary search tree is implemented successfully.
