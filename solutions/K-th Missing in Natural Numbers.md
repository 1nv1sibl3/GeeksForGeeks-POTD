# K-th Missing in Natural Numbers

**Difficulty:** Medium

### Approach
- Sort the array in ascending order.
- Iterate through the elements.
- If `arr[i] <= k`, increment `k` because that number is missing from the remaining sequence.
- Otherwise, stop and return `k`.

### Python Solution

```python
class Solution:
    def findKthSmall(self, arr, k):
        arr.sort()

        for num in arr:
            if num <= k:
                k += 1
            else:
                break

        return k
```

### Complexity Analysis
- **Time Complexity:** `O(n log n)` – Sorting the array.
- **Auxiliary Space:** `O(1)` – In-place sorting.
