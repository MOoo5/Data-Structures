# Binary Tree Full Implementation in C++

This file contains the complete code for creating a binary tree and traversing it using Pre-order, In-order, and Post-order methods.

---

## Complete Code

```cpp
#include <iostream>
#include <algorithm> 
using namespace std;

// 1. Definition of the Node structure
struct Node {
    int data;
    Node* left;
    Node* right;

    // Constructor to create a new node
     Node(int val) {
        data = val;
        left = right = NULL;
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

// Tree Height
int tree_height(Node* r) {
    if (r == NULL)
        return -1;

    int l_height = tree_height(r->left);
    int r_height = tree_height(r->right);

    return max(l_height, r_height) + 1;
}

// Count Leaf Nodes
int getLeavesCount(Node* r) {
    if (r == NULL)
        return 0;

    if (r->left == NULL && r->right == NULL)
        return 1;

    return getLeavesCount(r->left) + getLeavesCount(r->right);
}

// Count All Nodes
int size(Node* r) {
    if (r == NULL)
        return 0;

    return size(r->left) + 1 + size(r->right);
}

// Search
bool search(Node* root, int key) {
    if (root == NULL)
        return false;

    if (root->data == key)
        return true;

    return search(root->left, key) || search(root->right, key);
}

int main() {

  
    /*
                5
              /   \
            15     9
           /      / \
          3      2   11
    */

    Node* root = new Node(5);

    root->left = new Node(15);
    root->left->left = new Node(3);

    root->right = new Node(9);
    root->right->left = new Node(2);
    root->right->right = new Node(11);

    cout << "Preorder: ";
    preOrder(root);

    cout << "\nInorder: ";
    inOrder(root);

    cout << "\nPostorder: ";
    postOrder(root);

    cout << "\n\nTree Height = " << tree_height(root);

    cout << "\nTree Nodes Count = " << size(root);

    cout << "\nTree Leaves Count = " << getLeavesCount(root);

    root = NULL;

    cout << "\n\nAfter making root NULL:";
    cout << "\nTree Height = " << tree_height(root);

    return 0;
}
```