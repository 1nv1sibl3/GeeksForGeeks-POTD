## Approach
There are only two possible alternating patterns: `010101...` and `101010...`. Count the flips needed for both patterns and return the minimum.

## Solution
```python
class Solution:
    def minFlips(self, s):
        flips1 = flips2 = 0
        
        for i in range(len(s)):
            if s[i] != ('0' if i % 2 == 0 else '1'):
                flips1 += 1
            if s[i] != ('1' if i % 2 == 0 else '0'):
                flips2 += 1
                
        return min(flips1, flips2)
```

## Complexity
- **Time:** O(n)
- **Space:** O(1)
