# Geek's Destination with Special Jump

**Difficulty:** Hard

## Approach

- Each complete movement cycle gives a net displacement of `a - b`.
- For a jump of length `j`, Geek must first reach `x = d - j`.
- The minimum number of complete cycles required is:

  `c = max(0, ceil((x - a) / (a - b)))`

- The minimum time becomes:

  `T(x) = x + 2 * b * c + 1`

- Instead of iterating over every jump length, calculate
  the prefix sum of `T(x)` using arithmetic progressions.
- The final answer is:

  `F(d - l) - F(d - r - 1)`

- Return the result modulo `10^9 + 7`.

## Complexity

- **Time Complexity:** O(1)
- **Auxiliary Space:** O(1)


```py
class Solution:
    def minTime(self, a: int, b: int, d: int, l: int, r: int) -> int:
        MOD = 10**9 + 7
        k = a - b

        def prefix(x):
            if x <= 0:
                return 0

            if x <= a:
                return x * (x + 3) // 2

            ans = a * (a + 3) // 2
            n = x - a

            q, rem = divmod(n, k)

            ans += n * (2 * a + n + 3) // 2
            ans += 2 * b * (k * q * (q + 1) // 2 + rem * (q + 1))

            return ans

        return (prefix(d - l) - prefix(d - r - 1)) % MOD
```
