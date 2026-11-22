# Longest Subarray Sum Divisible by K

## Approach
Used prefix sums and a hash map to store the first occurrence of each remainder. If a remainder repeats, the sum of the elements between those indices is divisible by K.

## Complexity
- Time: O(n)
- Space: O(min(n, k))

## Code
```py
class Solution:
    def longestSubarrayDivK(self, arr, k):
        rem_index = {0: -1}
        prefix_sum = 0
        max_len = 0

        for i in range(len(arr)):
            prefix_sum += arr[i]
            rem = prefix_sum % k

            if rem in rem_index:
                max_len = max(max_len, i - rem_index[rem])
            else:
                rem_index[rem] = i

        return max_len
