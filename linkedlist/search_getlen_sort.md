# Additional Linked List Operations

These functions complete the utility of the list by adding searching, counting, and sorting capabilities:
* **search**: Performs a linear search to find an element ($O(n)$).
* **get_len**: Returns the current number of elements ($O(1)$).
* **sort_list**: Sorts the list in ascending order using a Bubble Sort approach ($O(n^2)$).

### Source Code

```cpp
#include<bits/stdc++.h>
using namespace std;

// 1. Implement a linked list with the following operations:   
class linkedlist{

struct node
{
    int num ; 
    node *next_node;
};

node *first , *last;
int len ;

public:
linkedlist(){
    first = last = NULL;
  len = 0 ;
}

  
// h. Search for an element in the list and return true if found, false otherwise.
bool search(int elem) {
    node *cur = first;

    while (cur != NULL) {
        if (cur->num == elem) {
            return true;
        }
        cur = cur->next_node;
    }
    return false;
}

// i. Count the number of elements in the list.
int get_len() {
    return len;
}

// j. Sort the elements of the list in ascending order.
void sort_list() {
    if (first == NULL) return; // Boundary check for empty list

    for (node *i = first; i != NULL; i = i->next_node) {
        for (node *j = i->next_node; j != NULL; j = j->next_node) {
            if (i->num > j->num) {
                swap(i->num, j->num); // Efficient swapping of values
            }
        }
    }
}


};
```