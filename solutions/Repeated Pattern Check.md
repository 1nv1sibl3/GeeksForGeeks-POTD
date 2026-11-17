## Approach
Traverse the string and count consecutive `x`s followed by consecutive `y`s. If their counts differ, return `False`. Repeat until the string ends.

## Code

```python
class Solution:
    def findPattern(self, s):
        i, n = 0, len(s)

        while i < n:
            x = y = 0

            while i < n and s[i] == 'x':
                x += 1
                i += 1

            while i < n and s[i] == 'y':
                y += 1
                i += 1

            if x == 0 or x != y:
                return False

        return True
```

## Complexity
- **Time:** O(n)
- **Space:** O(1)
