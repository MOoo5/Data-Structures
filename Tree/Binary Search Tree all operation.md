# Binary Search Tree (BST) - Full Implementation in C++

## Overview

A **Binary Search Tree (BST)** is a special type of Binary Tree where:

- Every node contains a value.
- Values smaller than the current node go to the **left subtree**.
- Values greater than the current node go to the **right subtree**.

This property makes searching, insertion, and deletion more efficient compared to a normal binary tree.

---

# Features Implemented

This implementation includes:

- Insert Nodes
- Search for a Node
- Find Minimum Node
- Delete Nodes
- Calculate Tree Height
- Count Total Nodes
- Count Leaf Nodes
- Tree Traversals
  - Preorder
  - Inorder
  - Postorder
- Copy the Entire Tree
- Count Levels

---

# Complete Code (C++)

```cpp
#include<bits/stdc++.h>
using namespace std;

struct Node{
    int data;
    Node* left;
    Node* right;
};

// Insert an item in the binary search tree
Node* insert_items(Node*& root, int item){

    if(root == nullptr){

        Node* newNode = new Node;

        newNode->data = item;
        root = newNode;

        root->left = root->right = nullptr;
    }

    else{

        if(item <= root->data){
            root->left = insert_items(root->left, item);
        }

        if(item > root->data){
            root->right = insert_items(root->right, item);
        }
    }

    return root;
}

// Search the binary search tree for a particular item
bool search_item(Node*& root, int key){

    if(root == nullptr){
        cout << "empty tree";
        return 0;
    }

    if(root->data == key)
        return 1;

    if(key < root->data)
        return search_item(root->left, key);

    else
        return search_item(root->right, key);
}

// Find the minimum item in Binary Search Tree
Node* Find_min(Node*& root){

    while(root->left != nullptr){
        root = root->left;
    }

    return root;
}

// Delete an item from the binary search tree
Node* delete_item(Node*& root, int key){

    if(root == nullptr){
        return nullptr;
    }

    if(key < root->data){
        root->left = delete_item(root->left, key);
    }

    else if(key > root->data){
        root->right = delete_item(root->right, key);
    }

    else{

        // Case 1: Leaf Node
        if(root->left == nullptr && root->right == nullptr){

            delete root;
            return nullptr;
        }

        // Case 2: Node has one child
        else if(root->left == nullptr){

            Node* temp = root->right;
            delete root;

            return temp;
        }

        else if(root->right == nullptr){

            Node* temp = root->left;
            delete root;

            return temp;
        }

        // Case 3: Node has two children
        else{

            Node* temp = Find_min(root->right);

            root->data = temp->data;

            root->right = delete_item(root->right, temp->data);
        }
    }

    return root;
}

// Find the height of the binary search tree
int height_of_tree(Node*& root){

    if(root == nullptr)
        return 0;

    return 1 + max(
        height_of_tree(root->left),
        height_of_tree(root->right)
    );
}

// Find the number of nodes in the binary search tree
int num_of_nodes(Node*& root){

    if(root == nullptr)
        return 0;

    return 1 +
           num_of_nodes(root->left) +
           num_of_nodes(root->right);
}

// Find the number of leaves in the binary search tree
int count_leaves(Node* root){

    if(root == nullptr)
        return 0;

    if(root->right == nullptr &&
       root->left == nullptr){

        return 1;
    }

    return count_leaves(root->left) +
           count_leaves(root->right);
}

// Traverse of Binary Search Tree (Preorder Traverse)
void pre_order(Node*& root){

    if(root == nullptr){
        return;
    }

    cout << root->data << ' ';

    pre_order(root->left);
    pre_order(root->right);
}

// Traverse of Binary Search Tree (Inorder Traverse)
void In_order(Node*& root){

    if(root == nullptr)
        return;

    In_order(root->left);

    cout << root->data << ' ';

    In_order(root->right);
}

// Traverse of Binary Search Tree (Postorder Traverse)
void post_order(Node*& root){

    if(root == nullptr)
        return;

    post_order(root->left);
    post_order(root->right);

    cout << root->data << ' ';
}

// Copy the binary search tree
Node* copy_tree(Node*& root){

    if(root == nullptr)
        return nullptr;

    Node* newNode = new Node;

    newNode->data = root->data;

    newNode->left = newNode->right = nullptr;

    newNode->left = copy_tree(root->left);
    newNode->right = copy_tree(root->right);

    return newNode;
}

// Count levels in the tree
int count_levels(Node*& root){

    if(root == nullptr)
        return 0;

    int height = count_levels(root->left);
    int heightR = count_levels(root->right);

    return 1 + max(height, heightR);
}

int main(){

    Node* root = NULL;

    // Insert
    root = insert_items(root, 10);
    root = insert_items(root, 5);
    root = insert_items(root, 20);
    root = insert_items(root, 3);
    root = insert_items(root, 7);

    // Traversals
    cout << "InOrder: ";
    In_order(root);
    cout << endl;

    cout << "PreOrder: ";
    pre_order(root);
    cout << endl;

    cout << "PostOrder: ";
    post_order(root);
    cout << endl;

    // Search
    cout << "\nSearch 7: "
         << (search_item(root, 7)
         ? "Found"
         : "Not Found")
         << endl;

    // Height
    cout << "Height: "
         << height_of_tree(root)
         << endl;

    // Number of Nodes
    cout << "Number of Nodes: "
         << num_of_nodes(root)
         << endl;

    // Leaf Nodes
    cout << "Leaf Nodes: "
         << count_leaves(root)
         << endl;

    // Copy Tree
    Node* newRoot = copy_tree(root);

    cout << "\nCopied Tree (InOrder): ";

    In_order(newRoot);

    cout << endl;

    // Delete
    root = delete_item(root, 5);

    cout << "\nAfter Deleting 5 (InOrder): ";

    In_order(root);

    cout << endl;

    return 0;
}
```

---

# BST Important Rules

## Left Subtree
Contains values smaller than the parent node.

---

## Right Subtree
Contains values greater than the parent node.

---

## Inorder Traversal
Always prints BST elements in **sorted order**.

---

# Time Complexity

| Operation | Average Case | Worst Case |
|-----------|--------------|-------------|
| Insert    | `O(log n)`   | `O(n)`      |
| Search    | `O(log n)`   | `O(n)`      |
| Delete    | `O(log n)`   | `O(n)`      |

> Worst case happens when the tree becomes skewed like a linked list.