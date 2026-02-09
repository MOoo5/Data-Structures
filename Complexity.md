# Complexity in Data Structures and Algorithms

## Introduction
Complexity in data structures is a fundamental concept in computer science that helps us analyze the performance and efficiency of algorithms. It allows us to quantify the resources (such as time and memory) required by an algorithm to solve a problem as the input size grows. In this article, we’ll explore the basics of complexity, including time and space complexity, and how they impact algorithm design.

In search algorithms, analyzing efficiency requires considering different potential scenarios:

* **Base Case (Omega notation $\Omega$):** Denotes the simplest input where the algorithm terminates in the least number of steps. Often denoted by $O(1)$ (constant time).
* **Average Case (Theta notation $\Theta$):** Represents the performance expected on average when considering all possible inputs. For example, linear search has an average case of $O(n/2)$.
* **Worst Case (Big O notation $O$):** Represents the most challenging scenario, requiring the maximum number of steps. Linear search’s worst case is $O(n)$.

---

## Big O notation
Big O notation is a mathematical tool used to describe the **upper bound** of how an algorithm’s execution time or space complexity grows as the input size ($n$) increases.

### Key notations:
* **$O(1)$:** Constant time. Execution time is independent of input size.
* **$O(\log n)$:** Logarithmic growth. Very efficient; doubling the input only adds a constant amount of time.
* **$O(n)$:** Linear growth. Time grows proportionally to the input size.
* **$O(n^2)$:** Quadratic growth. Common in nested loops.
* **$O(k^n)$:** Exponential growth. Generally undesirable due to rapid time increase.

---

## Complexity Analysis Examples

### Example 1: Simple Summation Loop
```cpp
sum = 0; // n = 5
for (i = 1; i <= n; i++)
    sum = sum + 1;
```
| Step           | Description                         | Time Complexity |
|----------------|-------------------------------------|-----------------|
| Initialization | Declare variables sum and i         | O(1)            |
| Loop           | Iterate n times                     | O(n)            |
| Increment      | Add 1 to sum in each iteration       | O(n)            |
| Total          |                                     | O(n)            |


## Example 2: Printing Loop
```cpp
int i;
i = 0;
for (i = 0; i < n; i++) {
    print i;
}
```
`Total Complexity`: $O(n)$. Each iteration takes constant time, and the loop runs $n$ times.


## Example 3: Nested Loops (Quadratic)
```cpp
int i;
i = 0;
for (i = 0; i < n; i++) {
    print i;
}
for (j = 0; j < n; j++) {
    for (int k = 0; k < n; k++)
        print j + k;
}
```
| Step        | Description                    | Time Complexity |
|-------------|--------------------------------|-----------------|
| Outer loop  | Iterate n times                | O(n)            |
| Inner loop  | Iterate n² times               | O(n²)           |
| Operations  | Constant time actions          | O(1)            |
| Total       |                                | O(n²)           |



## Example 4: Logarithmic Growth

```cpp
int i;
i = 1;
for (i; i < n; i = i * 2)
    print i;
```
`Total Complexity`: $O(\log n)$. Since `i` doubles every time, it reaches `n` in $\log_2(n)$ steps.

## Example 5: Mixed Linear and Logarithmic
```cpp
int i;
i = j = 0;
for (i; i < n; i++)
    for (j; j < n; j = j / 3)
        print i + j;
```
`Total Complexity`: Roughly $O(n \cdot \log_3 n)$. The outer loop is linear, and the inner loop decreases $j$ by a factor of 3.

## Example 6: Triple Nested Loops
```cpp
for (int i = 0; i < n; i++)
    for (int j = 0; j < n; j++)
        for (int k = 0; k < n; k = k * 2)
            print i + j + k;
```
`Total Complexity`: $O(n^2 \cdot \log n)$. Two linear loops ($n \times n$) and one logarithmic loop ($\log n$).

## Example 7: Complex Multi-Loop
```cpp
for (int i = n / 2; i < n; i++)          // n/2 iterations
    for (int k = 0; k < n; k = k * 2)    // log n iterations
        for (int j = 0; j < n; j = j * 2) // log n iterations
            print i + j + k;
```
`Total Complexity`: $O(n \cdot \log^2 n)$.

## Fibonacci Sequence
The Fibonacci sequence: $0, 1, 1, 2, 3, 5, 8, 13, \dots$Defined as: $F(n) = F(n-1) + F(n-2)$

## Example 8: Recursive Fibonacci
```cpp
int fib(int n) {
    if (n < 2)
        return n;
    return fib(n - 1) + fib(n - 2); 
}
```
`Total Complexity`: $O(2^n)$. In Big O notation, this recursive implementation signifies exponential growth, as the number of function calls roughly doubles with each increase in $n$.