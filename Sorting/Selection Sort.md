## 2. Selection Sort

**The Idea:** In each iteration, find the minimum element in the unsorted portion and place it at the beginning.

**Analogy:** Like selecting the smallest person from a group and placing them first, then repeating.

**Time Complexity:**
- Best Case: O(n²)
- Average Case: O(n²)
- Worst Case: O(n²)

**Space Complexity:** O(1)

**Code:**

```cpp
void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int minIdx = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIdx]) {
                minIdx = j;
            }
        }
        swap(arr[i], arr[minIdx]);
    }
}
```

---