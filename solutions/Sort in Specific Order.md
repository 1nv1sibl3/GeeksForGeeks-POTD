# Sort in Specific Order

## Approach
- Separate the array into odd and even numbers.
- Sort odd numbers in descending order.
- Sort even numbers in ascending order.
- Concatenate both lists and update the original array.

## Solution
```python
class Solution:
    def sortIt(self, arr):
        odd = []
        even = []

        for num in arr:
            if num % 2:
                odd.append(num)
            else:
                even.append(num)

        odd.sort(reverse=True)
        even.sort()

        arr[:] = odd + even
        return arr