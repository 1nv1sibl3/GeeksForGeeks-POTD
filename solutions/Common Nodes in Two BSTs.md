# Common Nodes in Two BSTs

**Difficulty:** Medium  
**Platform:** GeeksforGeeks  
**Topic:** Binary Search Trees, Stack, Inorder Traversal

## Approach

Use two stacks to perform simultaneous inorder traversal of both BSTs.

- Push left nodes into their respective stacks.
- Compare the top elements of both stacks.
- If equal, add the value to the result and move both traversals forward.
- If one value is smaller, advance that BST.
- Continue until both traversals are complete.

Since inorder traversal of a BST produces sorted values, this efficiently finds all common nodes in sorted order.

## Python Solution

```python
class Solution:
    def findCommon(self, r1: 'Node', r2: 'Node') -> list[int]:
        s1, s2 = [], []
        ans = []

        while r1 or r2 or s1 or s2:
            while r1:
                s1.append(r1)
                r1 = r1.left

            while r2:
                s2.append(r2)
                r2 = r2.left

            if s1 and s2:
                if s1[-1].data == s2[-1].data:
                    ans.append(s1[-1].data)
                    r1 = s1.pop().right
                    r2 = s2.pop().right

                elif s1[-1].data < s2[-1].data:
                    r1 = s1.pop().right

                else:
                    r2 = s2.pop().right

            elif s1:
                r1 = s1.pop().right

            elif s2:
                r2 = s2.pop().right

        return ans
```

## Complexity Analysis

- **Time Complexity:** `O(N + M)` — Each node is visited at most once.
- **Auxiliary Space:** `O(H1 + H2)` — Two stacks for inorder traversal.

Where `N` and `M` are the sizes of the two BSTs, and `H1` and `H2` are their respective heights.
