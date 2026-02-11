
```cpp
#include <bits/stdc++.h>
using namespace std;
#define ll long long


bool isPair(char open, char clos) { // Function to check if the opening and closing brackets are of the same type
    return (open == '(' && clos == ')') ||(open == '{' && clos == '}') || (open == '[' && clos == ']');
}

bool areBalanced(string ex) { // Function to check if the brackets in the expression are balanced

    stack<char> st;

for(int i = 0 ; i < ex.size(); ++i){

    if(ex[i] == '(' || ex[i] == '{' || ex[i] == '['){
        st.push(ex[i]);
    }

    else if(ex[i] == ')' || ex[i] == '}' || ex[i] == ']'){

        if(st.empty() || !isPair(st.top(), ex[i])){
            return false;
        }

         else{
            st.pop();
        }

    }
}
    return st.empty(); // If stack is empty, brackets are balanced
}


signed main() {

    string ex;  cin >> ex;

    if(areBalanced(ex)){
        cout << "Balanced" << endl;
    }


    else{
        cout << "Not Balanced" << endl;
    }
   
}


```
# Balanced Parentheses Checker using Stack

This C++ program determines whether a given string of parentheses (brackets) is "balanced." A balanced string means every opening bracket has a corresponding closing bracket of the same type, and they are closed in the correct order.

## 1. Core Logic (The Algorithm)
The code utilizes the **Stack** data structure based on the **LIFO** (Last-In-First-Out) principle:
* **Opening Brackets:** When the program encounters `(`, `{`, or `[`, it **pushes** them onto the stack.
* **Closing Brackets:** When it encounters `)`, `}`, or `]`, it checks the **top** of the stack.
    * If the stack is empty or the top element doesn't match the closing bracket, the string is **Not Balanced**.
    * If they match, it **pops** the top element and continues.
* **Final Result:** After scanning the entire string, if the stack is **empty**, the string is balanced.



---

## 2. Function Breakdown

### `isPair(char open, char clos)`
A helper function that returns `true` if the two characters are matching pairs (e.g., `(` and `)`), and `false` otherwise.

### `areBalanced(string ex)`
The main logic function:
1.  Loops through the string once.
2.  Handles the **Push** and **Pop** logic described above.
3.  Returns `st.empty()` to ensure no leftover unclosed brackets remain.

---

## 3. Complexity Analysis

| Complexity Type | Notation | Reason |
| :--- | :--- | :--- |
| **Time Complexity** | $O(n)$ | We iterate through the string of length $n$ exactly once. |
| **Space Complexity** | $O(n)$ | In the worst case (e.g., all opening brackets), the stack will store $n$ characters. |

---

## 4. Execution Example (Dry Run)
**Input:** `{[()]}`

1.  Read `{` $\rightarrow$ Stack: `[` **{** `]`
2.  Read `[` $\rightarrow$ Stack: `[` **{ , [** `]`
3.  Read `(` $\rightarrow$ Stack: `[` **{ , [ , (** `]`
4.  Read `)` $\rightarrow$ Matches `(` at top $\rightarrow$ **Pop** $\rightarrow$ Stack: `[` **{ , [** `]`
5.  Read `]` $\rightarrow$ Matches `[` at top $\rightarrow$ **Pop** $\rightarrow$ Stack: `[` **{** `]`
6.  Read `}` $\rightarrow$ Matches `{` at top $\rightarrow$ **Pop** $\rightarrow$ Stack: **Empty**
7.  **Result:** **Balanced** ✅

