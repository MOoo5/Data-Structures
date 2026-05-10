# Binary Tree Traversal Methods

There are three main types of tree traversals: **Pre-order**, **Post-order**, and **In-order**.

---

## 1. Post-order Traversal
**The Principle:** Left $\rightarrow$ Right $\rightarrow$ Root.
For every subtree, we repeat the same logic recursively.

*   **Logic:** Visit the left child, then the right child, and finally the root node.
*   **Visual Shortcut:** To verify the output, draw a line from the **right side** of each node. Connect them following the traversal path.

### Code Implementation:
```cpp
void postOrder(Node* root) {
    if (root == NULL) return;
    postOrder(root->left);
    postOrder(root->right);
    cout << root->data << " ";
}
```

## 2. Pre-order Traversal

**The Principle:** Root → Left → Right

For every subtree, we repeat the same logic recursively.

* **Logic:** Visit the root node first, then the left child, and finally the right child.

* **Visual Shortcut:** To verify the output, draw a line from the left side of each node. Connect them following the traversal path.

### Code Implementation:

```cpp
void preOrder(Node* root) {
    if (root == NULL) return;
    cout << root->data << " ";
    preOrder(root->left);
    preOrder(root->right);
}
```

---

## 3. In-order Traversal

**The Principle:** Left → Root → Right

For every subtree, we repeat the same logic recursively.

* **Logic:** Visit the left child, then the root node, and finally the right child.

* **Visual Shortcut:** To verify the output, draw a line downwards from the bottom of each node. Connect them following the traversal path.

### Code Implementation:

```cpp
void inOrder(Node* root) {
    if (root == NULL) return;
    inOrder(root->left);
    cout << root->data << " ";
    inOrder(root->right);
}
```

---

## Quick Summary

| Type | Order | Common Use |
|---|---|---|
| **Pre-order** | Root → Left → Right | Tree copying, Prefix expression |
| **In-order** | Left → Root → Right | BST sorted output |
| **Post-order** | Left → Right → Root | Tree deletion, Postfix expression |