# Max Equal Sum in 3 Stacks

**Difficulty:** Medium  
**Platform:** GeeksforGeeks

## Approach
Use a greedy approach with three pointers. Calculate the initial sum of each stack and repeatedly remove the top element from the stack with the maximum sum until all three sums become equal.

If any stack gets exhausted before equality is achieved, return `0`.

## Solution (Python)

```python
class Solution:
    def maxEqualSum(self, s1: list[int], s2: list[int], s3: list[int]) -> int:
        sum1, sum2, sum3 = sum(s1), sum(s2), sum(s3)
        i = j = k = 0

        while True:
            if sum1 == sum2 == sum3:
                return sum1

            if sum1 >= sum2 and sum1 >= sum3:
                if i == len(s1):
                    return 0
                sum1 -= s1[i]
                i += 1

            elif sum2 >= sum1 and sum2 >= sum3:
                if j == len(s2):
                    return 0
                sum2 -= s2[j]
                j += 1

            else:
                if k == len(s3):
                    return 0
                sum3 -= s3[k]
                k += 1
```

## Complexity Analysis
- **Time Complexity:** `O(n1 + n2 + n3)` — Each element is processed at most once.
- **Space Complexity:** `O(1)` — Uses only three pointers and sum variables.
