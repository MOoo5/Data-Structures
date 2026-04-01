# Linked List Implementation in C++

This code demonstrates a basic **Singly Linked List** with essential operations:
* **add_first**: Inserts a new node at the beginning of the list ($O(1)$).
* **add_last**: Inserts a new node at the end of the list using the `last` pointer ($O(1)$).
* **add_atpos**: Inserts a new node at a specific index by traversing the list ($O(n)$).
* **print**: Displays all elements in the list.



### Source Code

```cpp
#include <iostream>
#include <bits/stdc++.h>

using namespace std;

class linkedlist {

    struct node {
        int num;
        node *next_node;
    };

    node *first, *last;
    int len;

public:
    linkedlist() {
        first = last = NULL;
        len = 0;
    }

    // a. Add an element at the beginning of the list.
    void add_first(int element) {
        node *new_node = new node;
        new_node->num = element;

        if (len == 0) {
            first = last = new_node;
            new_node->next_node = NULL;
        } else {
            new_node->next_node = first;
            first = new_node;
        }
        len++;
    }

    // b. Add an element at the end of the list.
    void add_last(int element) {
        node *new_node = new node;
        new_node->num = element;
        new_node->next_node = NULL;

        if (len == 0) {
            first = last = new_node;
        } else {
            last->next_node = new_node;
            last = new_node;
        }
        len++;
    }

    // c. Add an element at a specific position in the list.
    void add_atpos(int pos, int elem) {
        if (pos < 0 || pos > len) {
            cout << "Out Of Range\n";
            return;
        }

        if (pos == 0) {
            add_first(elem);
        } else if (pos == len) {
            add_last(elem);
        } else {
            node *new_node = new node;
            new_node->num = elem;

            node *cur = first;
            // Iterate to the node just before the target position
            for (int i = 1; i < pos; ++i) {
                cur = cur->next_node;
            }
            new_node->next_node = cur->next_node;
            cur->next_node = new_node;
            len++;
        }
    }

    // d. Print the elements of the list.
    void print() {
        node *cur = first;
        while (cur != NULL) {
            cout << cur->num << ' ';
            cur = cur->next_node;
        }
        cout << endl;
    }
};

int main() {
    linkedlist l;

    l.add_first(10);   // List: 10
    l.add_last(20);    // List: 10 20
    l.add_first(0);    // List: 0 10 20
    l.add_atpos(1, 5); // List: 0 5 10 20

    l.print(); // Expected Output: 0 5 10 20

    return 0;
}