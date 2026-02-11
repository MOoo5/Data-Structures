# Stack Applications: Expression Logic

## 1. Infix to Postfix Conversion
**Infix:** `A + B * C` (How humans write)
**Postfix:** `A B C * +` (How computers process)

### **The Role of the Stack**
The stack is used to temporarily store **operators** until their precedence allows them to be added to the output.

* **Operands (A, B, 1, 2):** Add directly to the **Output**.
* **Left Parenthesis `(`:** Always **Push** to the stack.
* **Right Parenthesis `)`:** **Pop** everything from the stack to the output until a `(` is found.
* **Operators ($+, -, \times, \div$):**
    * If the current operator has **lower or equal precedence** than the one on Top of the stack, **Pop** the stack to the output.
    * Otherwise, **Push** the current operator.



---

## 2. Postfix Expression Evaluation
Evaluating a postfix expression like `5 3 +` results in `8`.

### **The Role of the Stack**
The stack is used to store **operands (numbers)** until an operator is encountered to perform the calculation.

1.  **Scan** the expression from **Left to Right**.
2.  **If a Number:** **Push** it onto the stack.
3.  **If an Operator:**
    * **Pop** the top two values (let them be `val2` and `val1`).
    * **Perform** the operation (`val1` *operator* `val2`).
    * **Push** the result back onto the stack.
4.  **Final Result:** The last remaining value in the stack is the answer.



---

## 3. Comparison Table

| Feature | Infix to Postfix | Postfix Evaluation |
| :--- | :--- | :--- |
| **Stack Stores** | Operators (`+`, `*`) | Operands (Numbers) |
| **Scanning Direction** | Left to Right | Left to Right |
| **Final Goal** | A string of symbols | A single numerical value |
| **Time Complexity** | $O(n)$ | $O(n)$ |