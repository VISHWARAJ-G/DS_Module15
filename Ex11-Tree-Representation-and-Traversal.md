# Ex11 - Tree Representation and Traversal

## DATE:

---

## AIM:
To write a C function to perform post order traversal of a binary tree.

---

## Algorithm

1. Start from the root node.  
2. Traverse the left subtree by recursively calling the postorder function.  
3. Traverse the right subtree by recursively calling the postorder function.  
4. Visit and print the current node's data.  
5. Repeat until the entire tree has been traversed in postorder.

---

## Program:

```c
/*
Program to perform post order traversal of a binary tree.
Developed by: Vishwaraj G,
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

void postorderTraversal(struct Node* root) {
    if (root == NULL)
        return;

    postorderTraversal(root->left);
    postorderTraversal(root->right);
    printf("%d ", root->data);
}

int main() {
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);

    printf("Postorder Traversal: ");
    postorderTraversal(root);
    printf("\n");

    return 0;
}
```
## Output:
```
Postorder Traversal: 4 5 2 3 1
```
## Result:
Thus, the function to perform post order traversal of a binary tree is implemented successfully.
