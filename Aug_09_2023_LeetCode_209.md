# 209. Minimum Size Subarray Sum

**Difficulty: Medium**

*Related Topics: Array, Binary Search, Sliding Window, Prefix Sum*

Given an array of positive integers nums and a positive integer target, return the minimal length of a 
subarray whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.

Example 1:

Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.

Example 2:

Input: target = 4, nums = [1,4,4]
Output: 1

Example 3:

Input: target = 11, nums = [1,1,1,1,1,1,1,1]
Output: 0

## Code

```python
from sys import maxsize
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        left, sum = 0, 0
        res = maxsize
        for i in range(len(nums)):
            sum += nums[i]
            while sum >= target:
                res = min(res, i - left + 1)
                sum -= nums[left]
                left += 1
        return res if res != maxsize else 0
```
