# Priority Queue: An Overview

A **Priority Queue** is a special type of queue where each element is associated with a priority. Unlike a standard Queue (FIFO), elements are served based on their priority.

## Key Characteristics

- **Highest Priority First:**  
  Elements with higher priority are dequeued before elements with lower priority.

- **Equal Priority:**  
  If two elements have the same priority, they are usually served according to their order in the queue (FIFO).

- **Usage:**  
  Widely used in:
  - Operating Systems (Load Balancing)
  - Huffman Coding
  - Graph algorithms like Dijkstra’s and Prim’s

---

# 1. Implementation using Arrays

In this approach, we use a fixed-size array of structures. Each structure holds the value and its priority.

## Operations

### Push (Enqueue)
Adds an element to the end of the array.  
**Time Complexity:** `O(1)`
```cpp
void push(int val, int p) {
    size++;
    pq[size].value = val;
    pq[size].priority = p;
}
```


### Peek
Scans the array to find the element with the highest priority.  
**Time Complexity:** `O(n)`

```cpp
int peek() {
    int highestPriority = -1;
    int index = -1;

    for (int i = 0; i <= size; i++) {
        if (highestPriority < pq[i].priority) {
            highestPriority = pq[i].priority;
            index = i;
        }
    }
    return index;
}
```

### Pop (Dequeue)
Finds the highest priority element, removes it, and shifts the remaining elements to fill the gap.  
**Time Complexity:** `O(n)`

```cpp
void pop() {
    int index = peek();

    // Shift elements to the left to fill the gap
    for (int i = index; i < size; i++) {
        pq[i] = pq[i + 1];
    }

    size--;
}
```


---

## Code Implementation (All Operation)

```cpp
#include <iostream>
using namespace std;

struct Element {
    int value;
    int priority;
};

Element pq[100];
int size = -1; // Current number of elements

// Add an element to the queue
void push(int val, int p) {
    size++;
    pq[size].value = val;
    pq[size].priority = p;
}

// Find the index of the highest priority element
int peek() {
    int highestPriority = -1;
    int index = -1;

    for (int i = 0; i <= size; i++) {
        if (highestPriority < pq[i].priority) {
            highestPriority = pq[i].priority;
            index = i;
        }
    }
    return index;
}

// Remove the highest priority element
void pop() {
    int index = peek();

    // Shift elements to the left to fill the gap
    for (int i = index; i < size; i++) {
        pq[i] = pq[i + 1];
    }

    size--;
}

int main() {
    push(10, 2);
    push(30, 5); // Highest Priority
    push(20, 3);

    cout << "Peek (Highest Priority): "
         << pq[peek()].value << endl;

    pop();

    cout << "Peek after pop: "
         << pq[peek()].value << endl;

    return 0;
}
```