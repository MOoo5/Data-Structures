## 5. Quick Sort

**The Idea:** Choose a pivot element, partition the array so all smaller elements are on the left and larger on the right, then sort both partitions.

**Analogy:** Like sorting people into two lines - shorter than 1 meter and taller than 1 meter, then sorting each line.

**Time Complexity:**
- Best Case: O(n log n)
- Average Case: O(n log n)
- Worst Case: O(n²) - when array is already sorted and pivot is always first/last

**Space Complexity:** O(log n) - due to recursion

**Code:**

```cpp
int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    
    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i + 1], arr[high]);
    return i + 1;
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
```

---