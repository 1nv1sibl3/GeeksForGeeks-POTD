# Any Duplicate Within K Distance

**Difficulty:** Easy\
**Approach:** Sliding Window + Hash Set

## Problem

Given an integer array `arr` and an integer `k`, determine whether any two distinct indices `i` and `j` exist such that:

- `arr[i] == arr[j]`
- `|i - j| <= k`

## Solution

```
class Solution:
    def checkWithinK(self, arr: list[int], k: int) -> bool:
        seen = set()

        for i in range(len(arr)):
            if arr[i] in seen:
                return True

            seen.add(arr[i])

            if len(seen) > k:
                seen.remove(arr[i - k])

        return False
```

## Approach

- Maintain a set of the previous `k` elements.
- Check whether the current element already exists in the set.
- If found, return `True`.
- Otherwise, add it to the set.
- Remove elements that fall outside the sliding window.

## Complexity Analysis

- **Time Complexity:** `O(n)` — Single traversal of the array.
- **Space Complexity:** `O(k)` — Stores at most `k` elements.

## Key Concept

Sliding Window + Hash Set for efficient duplicate detection.

Fix the window logic for duplicatesExplain the k equals zero case
