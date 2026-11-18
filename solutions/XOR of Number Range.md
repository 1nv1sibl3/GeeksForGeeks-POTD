## Approach: Prefix XOR

Use the repeating XOR pattern from `0` to `n`:

- `n % 4 == 0` → `n`
- `n % 4 == 1` → `1`
- `n % 4 == 2` → `n + 1`
- `n % 4 == 3` → `0`

The range XOR is calculated as `XOR(0, r) ^ XOR(0, l-1)` because common elements cancel out.

### Code (Python)

```python
class Solution:
    def findXOR(self, l: int, r: int) -> int:
        def xor(n):
            if n % 4 == 0:
                return n
            if n % 4 == 1:
                return 1
            if n % 4 == 2:
                return n + 1
            return 0

        return xor(r) ^ xor(l - 1)
```

**Time Complexity:** O(1)  
**Space Complexity:** O(1)
