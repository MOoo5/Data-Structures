# Binary Tree Full Implementation in C++

This file contains the complete code for creating a binary tree and traversing it using Pre-order, In-order, and Post-order methods.

---

## Complete Code

```cpp
#include <iostream>
using namespace std;

// 1. Definition of the Node structure
struct Node {
    int data;
    Node* left;
    Node* right;

    // Constructor to create a new node
    Node(int val) {
        data = val;
        left = NULL;
        right = NULL;
    }
};

// 2. Pre-order Traversal (Root -> Left -> Right)
void preOrder(Node* root) {
    if (root == NULL) return;
    cout << root->data << " "; // Visit Root
    preOrder(root->left);      // Visit Left
    preOrder(root->right);     // Visit Right
}

// 3. In-order Traversal (Left -> Root -> Right)
void inOrder(Node* root) {
    if (root == NULL) return;
    inOrder(root->left);       // Visit Left
    cout << root->data << " "; // Visit Root
    inOrder(root->right);      // Visit Right
}

// 4. Post-order Traversal (Left -> Right -> Root)
void postOrder(Node* root) {
    if (root == NULL) return;
    postOrder(root->left);      // Visit Left
    postOrder(root->right);     // Visit Right
    cout << root->data << " ";  // Visit Root
}

int main() {
    /* 
       Creating a sample tree:
              1
             / \
            2   3
           / \
          4   5
    */

    Node* root = new Node(1);
    root->left = new Node(2);
    root->right = new Node(3);
    root->left->left = new Node(4);
    root->left->right = new Node(5);

    cout << "Pre-order Traversal: ";
    preOrder(root);
    cout << endl;

    cout << "In-order Traversal: ";
    inOrder(root);
    cout << endl;

    cout << "Post-order Traversal: ";
    postOrder(root);
    cout << endl;

    return 0;
}
```