

```cpp
#include <bits/stdc++.h>
using namespace std;

const int Maxx = 100;

class Queue {
private:
    int arr[Maxx];
    int front, rear;

public:
    Queue() {
        front = -1;
        rear = -1;
    }

    bool isEmpty() {
        return front == -1;
    }

    bool isFull() {
        return rear == Maxx - 1;
    }

    void enqueue(int num) {
        if (!isFull()) {
            if (isEmpty()) front = 0; // أول عنصر
            rear++;
            arr[rear] = num;
        } else {
            cout << "Queue is Full\n";
        }
    }

    void dequeue() {
        if (!isEmpty()) {
            if (front == rear) {
                // آخر عنصر → رجّع الـ queue لحالتها الأولى
                front = -1;
                rear = -1;
            } else {
                front++;
            }
        } else {
            cout << "Queue is Empty\n";
        }
    }

    int peek() {
        if (!isEmpty())
            return arr[front];
        cout << "Queue is Empty\n";
        return -1;
    }
};

```