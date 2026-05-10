## 3. Insertion Sort

**The Idea:** Take each element and insert it into its correct position in the already sorted portion.

**Analogy:** Like sorting playing cards in your hand - you pick each card and place it in its correct position.

**Time Complexity:**
- Best Case: O(n) - when array is already sorted
- Average Case: O(n²)
- Worst Case: O(n²)

**Space Complexity:** O(1)

**Code:**

```cpp
void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```

---