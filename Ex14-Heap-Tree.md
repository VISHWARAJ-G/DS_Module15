# Ex14 - Heap Tree

## DATE: 20-03-2025

---

## AIM:
To write a C function to delete an element in a Heap Tree.

---

## Algorithm

1. Replace the root node (maximum element) with the last element in the heap.  
2. Decrease the size of the heap by one.  
3. Heapify the root node by comparing it with its largest child.  
4. Swap if the root is smaller than its largest child.  
5. Repeat the process until the heap property is restored.

---

## Program:

```c
/*
Program to delete an element in a Heap Tree
Developed by: 
RegisterNumber:  
*/

#include <stdio.h>

void heapify(int heap[], int n, int i) {
    int largest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && heap[left] > heap[largest])
        largest = left;

    if (right < n && heap[right] > heap[largest])
        largest = right;

    if (largest != i) {
        int temp = heap[i];
        heap[i] = heap[largest];
        heap[largest] = temp;
        heapify(heap, n, largest);
    }
}

int deleteRoot(int heap[], int n) {
    if (n <= 0) return -1;

    int root = heap[0];
    heap[0] = heap[n - 1];
    n--;

    heapify(heap, n, 0);

    return n;
}

void printHeap(int heap[], int n) {
    for (int i = 0; i < n; i++)
        printf("%d ", heap[i]);
    printf("\n");
}

int main() {
    int heap[] = {50, 30, 40, 10, 5, 20, 30};
    int n = sizeof(heap) / sizeof(heap[0]);

    printf("Original Heap:\n");
    printHeap(heap, n);

    n = deleteRoot(heap, n);

    printf("Heap after deleting root:\n");
    printHeap(heap, n);

    return 0;
}
```
## Output:
```
Original Heap:
50 30 40 10 5 20 30 
Heap after deleting root:
40 30 30 10 5 20 
```
## Result:
Thus, the function to delete an element in a Heap Tree is implemented successfully.
