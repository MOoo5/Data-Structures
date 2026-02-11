# Stack Implementation: Linked List vs. Array

## 1. What is Linked List Implementation?
In this approach, the stack is represented as a series of connected **Nodes**. Each node contains two parts:
* **Item:** The actual value you want to store.
* **Next:** A pointer/reference to the next node in the stack.

Unlike arrays, we don't use indexes. Instead, we use a **`top` pointer** that always points to the first node of the list. When you push a new item, it becomes the new head of the list.

---

## 2. Why use Linked List for a Stack?
We use this method primarily to overcome the limitations of the **Array** implementation:

* **Dynamic Sizing:** The stack can grow or shrink at runtime. You don't need to know the size of the data beforehand.
* **No "Stack Overflow":** Since it's dynamic, you will never run out of space as long as your system has available memory (RAM).
* **Memory Efficiency:** It only allocates memory when a new element is added, whereas an array reserves a large block of memory upfront regardless of whether it's used.

---

## 3. Comparison: Array vs. Linked List

| Feature | Array Implementation | Linked List Implementation |
| :--- | :--- | :--- |
| **Size** | Fixed (Static) - must be predefined. | Dynamic - grows and shrinks. |
| **Memory Allocation** | Allocated at compile time. | Allocated at runtime (Heap). |
| **Memory Usage** | Less memory per element (data only). | More memory per element (data + pointer). |
| **Performance** | Faster access (index-based). | Slightly slower due to pointer overhead. |
| **Overflow Risk** | High (happens when array is full). | Low (only if system memory is full). |

---

## 4. How Operations Work (Logic)

### **Push Operation**
1. Create a new node.
2. Set the new node's `next` to point to the current `top`.
3. Update the `top` pointer to point to this new node.

### **Pop Operation**
1. Check if the stack is empty (if `top == null`).
2. Create a temporary pointer to the current `top`.
3. Move the `top` pointer to the next node (`top = top->next`).
4. Delete/Free the temporary node.

---

**Would you like me to provide the C++ or Python code for this Linked List implementation?**# Stack Implementation: Linked List vs. Array

## 1. What is Linked List Implementation?
In this approach, the stack is represented as a series of connected **Nodes**. Each node contains two parts:
* **Data:** The actual value you want to store.
* **Next:** A pointer/reference to the next node in the stack.

Unlike arrays, we don't use indexes. Instead, we use a **`top` pointer** that always points to the first node of the list. When you push a new item, it becomes the new head of the list.

---

## 2. Why use Linked List for a Stack?
We use this method primarily to overcome the limitations of the **Array** implementation:

* **Dynamic Sizing:** The stack can grow or shrink at runtime. You don't need to know the size of the data beforehand.
* **No "Stack Overflow":** Since it's dynamic, you will never run out of space as long as your system has available memory (RAM).
* **Memory Efficiency:** It only allocates memory when a new element is added, whereas an array reserves a large block of memory upfront regardless of whether it's used.

---

## 3. Comparison: Array vs. Linked List

| Feature | Array Implementation | Linked List Implementation |
| :--- | :--- | :--- |
| **Size** | Fixed (Static) - must be predefined. | Dynamic - grows and shrinks. |
| **Memory Allocation** | Allocated at compile time. | Allocated at runtime (Heap). |
| **Memory Usage** | Less memory per element (data only). | More memory per element (data + pointer). |
| **Performance** | Faster access (index-based). | Slightly slower due to pointer overhead. |
| **Overflow Risk** | High (happens when array is full). | Low (only if system memory is full). |

---

## 4. How Operations Work (Logic)

### **Push Operation**
1. Create a new node.
2. Set the new node's `next` to point to the current `top`.
3. Update the `top` pointer to point to this new node.

### **Pop Operation**
1. Check if the stack is empty (if `top == null`).
2. Create a temporary pointer to the current `top`.
3. Move the `top` pointer to the next node (`top = top->next`).
4. Delete/Free the temporary node.

---


```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long

template <class t> 

class Stack {

    struct node{
        t item;
        node* next;
    };

    node* top , *cur;
public:
Stack(){
    top = NULL; 

}

void push (t item){
node* newnode = new node;   // create a new node 
newnode->item = item;       // assign the item to the new node
newnode->next = top;       // point the new node to the current top of the stack
top = newnode;              // update the top of the stack to be the new node
     
}

bool isEmpty(){
    return top == NULL;  // check if the stack is empty by checking if the top is NULL


}

void pop(){
    if (isEmpty()) {
        cout << "Stack is empty. Cannot pop." << endl;  // handle the case when trying to pop from an empty stack
        return;
    }

    node*temp = top;  // store the current top node in a temporary variable
    top = top->next;  // update the top of the stack to be the next
    delete temp;      // delete the old top node to free memory
}

void getTop( t &topItem){
    if (isEmpty()) {
        cout << "Stack is empty. No top element." << endl;  // handle the case when trying to get the top from an empty stack
        return;
    }
   else {
        topItem = top->item;  // assign the item of the current top node to the reference variable topItem
    }
}



void printStack() {
    cur = top;  // initialize the current pointer to the top of the stack

cout << "\nItems in the stack : ";
		cout << "[ ";
    while(cur!=NULL){  // loop through the stack until the current pointer is NULL
        cout << cur->item << " ";  // print the item of the current node
        cur = cur->next;  // move the current pointer to the next node in the

    }
    cout << " ]\n";
}

};





signed main() {
  Stack<int> s;  // create a stack of integers
  s.push(10);    // push 10 onto the stack
    s.push(20);    // push 20 onto the stack
    s.push(30);    // push 30 onto the stack
    s.printStack();  // print the contents of the stack
    int topItem;  // variable to hold the top item of the stack

    s.getTop(topItem);  // get the top item of the stack


    cout << "Top item: " << topItem << endl;  // print the top item

    s.pop();  // pop the top item from the stack


    s.printStack();  // print the contents of the stack after popping

   
}
```
