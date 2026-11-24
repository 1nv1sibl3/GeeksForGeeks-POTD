# Two Pairs with Same Sum

**Difficulty:** Medium  
**Platform:** GeeksforGeeks

## Approach

- Traverse all pairs in lexicographical order.
- Use a hash map to store the first pair for each sum.
- If the same sum appears again, check whether all four
  indices are distinct.
- Maintain the lexicographically smallest valid quadruplet.
- Return `[-1, -1, -1, -1]` if no valid quadruplet exists.

## Solution

```python
class Solution:
    def findPairs(self, arr: list[int]) -> list[int]:
        n = len(arr)
        seen = {}
        ans = None

        for c in range(n - 1):
            for d in range(c + 1, n):
                s = arr[c] + arr[d]

                pair = seen.get(s)

                if pair is None:
                    seen[s] = (c, d)
                else:
                    a, b = pair

                    if a != c and a != d and b != c and b != d:
                        curr = (a, b, c, d)

                        if ans is None or curr < ans:
                            ans = curr

                            if a == 0 and b == 1:
                                return list(ans)

        return list(ans) if ans else [-1, -1, -1, -1]
```

## Complexity Analysis

- **Time Complexity:** O(n²)
- **Space Complexity:** O(n²)

## Optimizations

- Stores only one pair per distinct sum.
- Avoids sorting and unnecessary list creation.
- Uses a single traversal of all possible pairs.
- Terminates early when the optimal first pair (0, 1)
  is found.
