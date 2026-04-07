

```cpp
#include <bits/stdc++.h>
using namespace std;

template <class t>
class Queue {
    struct node {
        t item;
        node* next;
    };

    node *front, *rear; // مؤشرين للبداية والنهاية
    int length;        // متغير اختياري لحساب عدد العناصر

public:
    Queue() {
        front = rear = NULL;
        length = 0;
    }


 bool isEmpty() {
        return front == NULL;
    }

    // إضافة عنصر (من الخلف - Rear)
    void enqueue(t item) {
        node* newNode = new node;
        newNode->item = item;
        newNode->next = NULL;

        if (isEmpty()) {
            // لو الطابور فاضي، الأول هو نفسه الأخير
            front = rear = newNode;
        } else {
            // نربط الأخير القديم بالجديد، ونخلي الجديد هو الـ rear
            rear->next = newNode;
            rear = newNode;
        }
        length++;
    }

   

    // مسح عنصر (من الأمام - Front)
    void dequeue() {
        if (isEmpty()) {
            cout << "Queue is empty. Cannot dequeue." << endl;
            return;
        }

        node* temp = front;
        if (front == rear) { // لو فيه عنصر واحد بس
            front = rear = NULL;
        } else {
            front = front->next; // حرك البداية للعنصر اللي بعده
        }
        delete temp;
        length--;
    }

    void getFront(t &frontItem) {
        if (isEmpty()) {
            cout << "Queue is empty." << endl;
            return;
        }
        frontItem = front->item;
    }

    void printQueue() {
        node* cur = front;
        cout << "\nItems in the Queue: [ ";
        while (cur != NULL) {
            cout << cur->item << " ";
            cur = cur->next;
        }
        cout << "]" << endl;
    }
};

int main() {
    Queue<int> q;
    q.enqueue(10); // أول واحد دخل
    q.enqueue(20);
    q.enqueue(30); // آخر واحد دخل
    
    q.printQueue();

    int firstItem;
    q.getFront(firstItem);
    cout << "Front item: " << firstItem << endl;

    q.dequeue(); // هيمسح الـ 10 (لأنها أول واحدة دخلت)
    cout << "After dequeue:";
    q.printQueue();

    return 0;
}
```