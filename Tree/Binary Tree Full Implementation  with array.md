# Binary Tree: Array Implementation & Traversal

This implementation uses a fixed-size array to represent a **Complete Binary Tree**.  
We navigate the tree using mathematical relationships between indices.

---

# Complete Code (C++)

```cpp
#include <iostream>
#include <algorithm> 
using namespace std;

// Global array for the tree
int tree[100];
int maxSize = 100;

// 1. Initialize the tree with -1 to indicate empty nodes
void initTree() {
    for (int i = 0; i < maxSize; i++) {
        tree[i] = -1;
    }
}

// 
void rootnode(int key) {
    if (tree[0] != -1)
        cout << "Tree already has a root\n";
    else
        tree[0] = key;
}

void leftchild(int key, int parent) {
    if (tree[parent] == -1)
        cout << "Can't set child at " << (parent * 2) + 1 << ", no parent found\n";
    else
        tree[(parent * 2) + 1] = key;
}

void rightchild(int key, int parent) {
    if (tree[parent] == -1)
        cout << "Can't set child at " << (parent * 2) + 2 << ", no parent found\n";
    else
        tree[(parent * 2) + 2] = key;
}

// 2. Traversal Operations
// ---------------------------------------------------------

// Pre-order: Root -> Left -> Right
void preOrder(int index) {
    if (index >= maxSize || tree[index] == -1)
        return;

    cout << tree[index] << " ";      // Root
    preOrder(2 * index + 1);         // Left Child
    preOrder(2 * index + 2);         // Right Child
}

// In-order: Left -> Root -> Right
void inOrder(int index) {
    if (index >= maxSize || tree[index] == -1)
        return;

    inOrder(2 * index + 1);          // Left
    cout << tree[index] << " ";      // Root
    inOrder(2 * index + 2);          // Right
}

// Post-order: Left -> Right -> Root
void postOrder(int index) {
    if (index >= maxSize || tree[index] == -1)
        return;

    postOrder(2 * index + 1);        // Left
    postOrder(2 * index + 2);        // Right
    cout << tree[index] << " ";      // Root
}

// ---------------------------------------------------------

int main() {
    initTree();

    /*
       Manually Building the Tree:

               10 (index 0)
              /  \
            20    30 (indices 1, 2)
           /  \
         40    50 (indices 3, 4)
    */

    tree[0] = 10; // Root
    tree[1] = 20; // Left of 10
    tree[2] = 30; // Right of 10
    tree[3] = 40; // Left of 20
    tree[4] = 50; // Right of 20

    cout << "--- Binary Tree Traversals (Array) ---\n" << endl;

    cout << "Pre-order Traversal:  ";
    preOrder(0); // Start from root at index 0
    cout << endl;

    cout << "In-order Traversal:   ";
    inOrder(0);
    cout << endl;

    cout << "Post-order Traversal: ";
    postOrder(0);
    cout << endl;

    return 0;
}
```

---

# Important Rules to Remember

## The Root
Always starts at index `0`.

---

## Left Child Location
For any node at index `i`, its left child is at:

```cpp
2 * i + 1
```

---

## Right Child Location
For any node at index `i`, its right child is at:

```cpp
2 * i + 2
```

---

## Parent Location
If you need to move upward, the parent of index `i` is at:

```cpp
(i - 1) / 2
```