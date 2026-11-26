# Range Vowel Count Queries

**Difficulty:** Medium  
**Approach:** Prefix Sum

## Solution

Instead of counting vowels for every query individually, we use a prefix sum array to store the cumulative vowel count.

- Initialize a prefix array of size `n + 1`.
- Traverse the string and update the prefix count whenever a vowel is encountered.
- For each query `[l, r]`, calculate the vowel count using `prefix[r + 1] - prefix[l]`.

## Python Code

```python
class Solution:
    def countVowels(self, s: str, queries: list[list[int]]) -> list[int]:
        vowels = set("aeiou")
        prefix = [0] * (len(s) + 1)

        for i, ch in enumerate(s):
            prefix[i + 1] = prefix[i] + (ch in vowels)

        return [prefix[r + 1] - prefix[l] for l, r in queries]
```

## Complexity Analysis

- **Time Complexity:** O(n + q)
- **Space Complexity:** O(n) (excluding the output array)

Where `n` is the length of the string and `q` is the number of queries.

Each query is answered in O(1) time after preprocessing.
