# **Character at Position in Infinite String**

**Difficulty:** Medium

## **Approach: Reverse Mapping**

Instead of constructing the infinite string, calculate its length until it reaches `pos`.

Then work backwards:

- If `pos` is in the first half, keep it unchanged.
- If `pos` falls within the `$` characters, return `$`.
- Otherwise, map `pos` to its mirrored position in the previous string.

Repeat until reaching the original string.

## **Python Solution**

```py

class Solution:
    def posInfinite(self, s: str, pos: int) -> str:
        n = len(s)
        length, i = n, 1

        while length < pos:
            length = 2 * length + i
            i += 1

        while i > 1:
            i -= 1
            prev = (length - i) // 2

            if prev < pos <= prev + i:
                return '$'

            if pos > prev + i:
                pos = length - pos + 1

            length = prev

        return s[pos - 1]

```

## **Complexity Analysis**

- **Time:** `O(log pos)` — Length doubles at each step.
- **Space:** `O(1)` — Only a few variables are used.

## **Example**

**Input:** `s = "abc", pos = 7`

First transformation: `abc$cba`

Position `7` maps to position `1` in the original string.

**Output:** `"a"`
