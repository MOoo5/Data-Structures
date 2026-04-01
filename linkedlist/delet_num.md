# Linked List Deletion Operations in C++

This section covers the core deletion operations for a **Singly Linked List**:
* **del_first**: Removes the head node and updates the `first` pointer ($O(1)$).
* **del_last**: Traverses the list to find the second-to-last node, then removes the last node ($O(n)$).
* **del_atpos**: Deletes a node at a specific index by re-linking the previous node to the next one ($O(n)$).



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

  
    // e. Delete an element from the beginning of the list.
void del_first(){
    if(len == 0){
        cout << "Empty List\n";
        return ;
    }

    else if(len == 1){
        delete first ;
        first = last = NULL;
    }

    else{
    node *temp = first ;
    first = first->next_node;
    delete temp ;
}
 len--;
}


// f. Delete an element from the end of the list.
void del_last(){
    if(len == 0){
        cout << "Empty List\n";
        return ;
    }

    else if(len == 1){
        delete first ;
        first = last = NULL;
    }

    else{
   node *cur = first->next_node , *prev = first ;
      
        while(cur != last){
            prev = cur ;
            cur = cur->next_node;
        }
        delete cur ;
        prev->next_node = NULL;
        last = prev ;
}

 len--;
}



 // g. Delete an element from a specific position in the list.
void del_atpos(int pos){
    if(pos < 0 || pos >= len ) {
         
        cout << "Out Of Range\n";
    }

    else{

        if(pos == 0){

            del_first();
        }

        else if(pos == len-1){

            del_last();
        }

        else{

    node *cur = first->next_node , *prev = first ;
    for(int i = 1 ; i < pos ; ++i){

        prev = cur ;
        cur = cur->next_node;
    }

    
    
    prev->next_node = cur->next_node;
    delete cur ;
   len--;
        }

    }
}


};
```
 