# Closest in BST

**Difficulty:** Medium  
**Platform:** GeeksforGeeks  
**Topic:** Binary Search Tree (BST)

## Problem
Find the minimum absolute difference between a given integer `k` and any node value in a BST.

## Approach
- Traverse the BST iteratively.
- Update the minimum absolute difference at each node.
- Move left if `k` is smaller, otherwise move right.
- Return `0` if an exact match is found.

## Complexity
- **Time:** O(h), where h is the height of the BST.
- **Space:** O(1)

## Solution (Python)

```python
class Solution:
    def minDiff(self, root: 'Node', k: int) -> int:
        ans = float('inf')

        while root:
            ans = min(ans, abs(root.data - k))

            if ans == 0:
                return 0

            if k < root.data:
                root = root.left
            else:
                root = root.right

        return ans
```
