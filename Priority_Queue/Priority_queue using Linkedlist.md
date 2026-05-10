# 2. Implementation using Linked List

This is a dynamic approach where we keep the list sorted based on priority during the push operation. This makes pop extremely fast.

---

## Operations

### Push (Enqueue)

Traverses the list to find the correct position for the new node so the list remains sorted.

**Time Complexity:** `O(n)`

```cpp
Node* push(Node* head, int d, int p) {
    Node* temp = new Node(d, p);


    if (head == NULL || p > head->priority) {
        temp->next = head;
        return temp;
    }

  
    Node* start = head;

    while (start->next != NULL &&
           start->next->priority >= p) {
        start = start->next;
    }

    temp->next = start->next;
    start->next = temp;

    return head;
}
```



---

### Peek

Simply returns the data of the head node.

**Time Complexity:** `O(1)`

```cpp
int peek(Node* head) {
    return head->data;
}
```



---

### Pop (Dequeue)

Removes the head node and updates the pointer.

**Time Complexity:** `O(1)`

```cpp
Node* pop(Node* head) {
    if (head == NULL)
        return NULL;

    Node* temp = head;
    head = head->next;

    delete temp; 

    return head;
}
```

---

# Code Implementation (ِAll Code)

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    int priority;
    Node* next;

    // Constructor to initialize a new node
    Node(int d, int p) {
        data = d;
        priority = p;
        next = NULL;
    }
};

// Insert a new node based on priority
Node* push(Node* head, int d, int p) {
    Node* temp = new Node(d, p);

    // Case 1:
    // List is empty or new node has higher priority than head
    if (head == NULL || p > head->priority) {
        temp->next = head;
        return temp;
    }

    // Case 2:
    // Traverse the list to find the right position
    Node* start = head;

    while (start->next != NULL &&
           start->next->priority >= p) {
        start = start->next;
    }

    temp->next = start->next;
    start->next = temp;

    return head;
}

// Remove the node with the highest priority (the head)
Node* pop(Node* head) {
    if (head == NULL)
        return NULL;

    Node* temp = head;
    head = head->next;

    delete temp; // Free memory

    return head;
}

// Get the highest priority value
int peek(Node* head) {
    return head->data;
}

int main() {
    Node* pq = NULL;

    pq = push(pq, 10, 1);
    pq = push(pq, 40, 4); // Highest Priority
    pq = push(pq, 20, 2);

    cout << "Highest Priority Element: "
         << peek(pq) << endl;

    pq = pop(pq);

    cout << "Next Element: "
         << peek(pq) << endl;

    return 0;
}
```

---

# Summary Comparison

| Operation | Array (Unsorted) | Linked List (Sorted) |
|-----------|------------------|----------------------|
| Push      | `O(1)`           | `O(n)`               |
| Pop       | `O(n)`           | `O(1)`               |
| Peek      | `O(n)`           | `O(1)`               |
| Space     | Fixed Size       | Dynamic (`new`)      |