# Smallest Subarray With Sum Greater Than X

## Approach: Sliding Window (Two Pointers)

Given an array of non-negative integers and an integer `x`, find the length of the smallest contiguous subarray whose sum is strictly greater than `x`.

### Python Solution

```python
class Solution:
    def smallestSubWithSum(self, arr, x):
        left = 0
        curr_sum = 0
        ans = float('inf')

        for right in range(len(arr)):
            curr_sum += arr[right]

            while curr_sum > x:
                ans = min(ans, right - left + 1)
                curr_sum -= arr[left]
                left += 1

        return ans if ans != float('inf') else 0
```

### Example

**Input:**
```python
x = 51
arr = [1, 4, 45, 6, 0, 19]
```

**Output:**
```python
3
```

**Explanation:** The smallest valid subarray is `[4, 45, 6]`, whose sum is `55` and length is `3`.

### Complexity Analysis

- **Time Complexity:** `O(n)` — Each element is visited at most twice.
- **Space Complexity:** `O(1)` — Constant extra space.

### Key Concept
Sliding Window works efficiently here because all array elements are non-negative, allowing the window to expand and shrink without losing track of possible minimum lengths.
