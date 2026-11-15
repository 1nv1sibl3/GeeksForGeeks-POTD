# Sum of All Digit Subsequences

## Problem
Given a string `s` consisting of digits, find the sum of all digits across all non-empty subsequences of `s`.

Return the answer modulo `10^9 + 7`.

## Approach – Contribution Technique

Instead of generating every possible subsequence, calculate how many times each digit contributes to the answer.

- For a string of length `n`, each digit can appear in exactly `2^(n-1)` subsequences.
- Therefore, the total answer is the sum of all digits multiplied by `2^(n-1)`.

### Formula

\[
Answer = \left(\sum digits\right) \times 2^{n-1} \mod (10^9+7)
\]

## Python Solution

```python
class Solution:
    def subsequenceSum(self, s):
        MOD = 10**9 + 7

        total = sum(int(digit) for digit in s)
        n = len(s)

        return (total * pow(2, n - 1, MOD)) % MOD
```

## Example

**Input:**
```text
s = "123"
```

**Output:**
```text
24
```

**Explanation:**

Each digit appears in `2^(3-1) = 4` subsequences.

Total = `(1 + 2 + 3) * 4 = 24`

## Complexity Analysis

- **Time Complexity:** `O(n + log n)` – Sum of digits and modular exponentiation.
- **Space Complexity:** `O(1)` – Constant extra space.

## Key Concept
Mathematical contribution technique + Modular Exponentiation.
