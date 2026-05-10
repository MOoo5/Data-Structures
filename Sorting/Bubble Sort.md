## 1. Bubble Sort

**The Idea:** Compare each pair of adjacent elements. If the first is greater than the second, swap them. Repeat until the array is sorted.

**Analogy:** Like bubbles rising to the surface - the largest element "floats" to the end in each iteration.

**Time Complexity:**
- Best Case: O(n) - when array is already sorted
- Average Case: O(n²)
- Worst Case: O(n²)

**Space Complexity:** O(1)

**Code:**

```cpp
void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
            }
        }
    }
}
```

---