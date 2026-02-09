# Introduction to Stack

## Overview
In the realm of computer science and programming, understanding data structures is fundamental. One such essential data structure is the **Stack**. This article delves into what stacks are, how they work, their operations, and their applications in programming.

---

## What is a Stack?
A stack is a linear data structure that follows the **Last-In-First-Out (LIFO)** principle. 

> **Analogy:** Imagine a stack of plates in a cafeteria; you can only take the top plate off the stack, and you add new plates only to the top. Similarly, in a stack data structure, elements can only be added or removed from the **top**.



---

## How Does a Stack Work?
A stack primarily revolves around two main actions:

1.  **Push:** Adds an element to the top of the stack.
2.  **Pop:** Removes the top element from the stack.

Additionally, stacks typically support:
* **Peek / getTop:** View the top element without removing it.
* **isEmpty:** Check if the stack contains any elements.

---

## Stack Implementation
Stacks are usually implemented in two ways:

| Implementation | Description |
| :--- | :--- |
| **Array Implementation** | Uses a fixed-size array. Push and pop operations modify the `top` index. |
| **Linked List Implementation** | Uses a dynamic linked list where each node is an element, and the `top` is the head of the list. |

---

## Detailed Operations
* **Push:** The new element becomes the top, and the stack size increases by one.
* **Pop:** The top element is returned or removed, and the stack size decreases by one.
* **getTop:** Returns the current top element without altering the stack.
* **isEmpty:** Returns `true` if the stack is empty, and `false` otherwise.

---

## Applications of Stacks
Stacks are used extensively in various computing scenarios:

* **Function Call Stack:** Manages function calls and local variables (recursion).
* **Expression Evaluation:** Used for infix-to-postfix conversion and solving arithmetic expressions.
* **Undo Mechanism:** Powers the "Undo" feature in text editors and design software.
* **Backtracking:** Crucial for algorithms like **Depth-First Search (DFS)** to explore paths.

---

## Conclusion
Stacks are simple yet powerful structures. Whether you are managing memory or implementing an undo button, mastering the stack is essential for building efficient software systems.


## Stack Code 

```cpp
#include <iostream>
using namespace std;

const int MAX_SIZE = 100;

class Stack {
private:
    int top;            // Index of the top element in the stack
    int item[MAX_SIZE]; // Array to store stack elements

public:
    // Constructor: Initializes top to -1 (empty stack)
    Stack() : top(-1) {}

    // Function to push an element onto the stack
    void push(int Element) {
        if (top >= MAX_SIZE - 1) {
            cout << "Stack is full on push" << endl;
        } else {
            top++;
            item[top] = Element;
        }
    }

    // Function to check if the stack is empty
    bool isEmpty() {
        return top < 0;
    }

    // Function to pop an element from the stack
    void pop() {
        if (isEmpty()) {
            cout << "Stack is empty on pop" << endl;
        } else {
            top--;
        }
    }

    // Function to get the top element of the stack
    void getTop(int& stackTop) {
        if (isEmpty()) {
            cout << "Stack is empty on getTop" << endl;
        } else {
            stackTop = item[top];
            cout << stackTop << endl;
        }
    }

    // Function to print the elements of the stack
    void print() {
        cout << "[";
        for (int i = top; i >= 0; i--) {
            cout << item[i] << " ";
        }
        cout << "]" << endl;
    }
};

int main() {
    Stack s;

    // Push elements onto the stack
    s.push(5);
    s.push(10);
    s.push(15);
    s.push(20);

    // Print the stack
    s.print();

    // Get and print the top element of the stack
    int y = 0;
    s.getTop(y);

    // Pop an element from the stack
    s.pop();

    // Push another element onto the stack
    s.push(7);

    // Print the stack again
    s.print();

    return 0;
}

```
