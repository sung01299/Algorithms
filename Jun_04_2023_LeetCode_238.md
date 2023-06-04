# 238. Product of Array Except Self

**Difficulty: Medium**

*Related Topics: Array, Prefix Sum*

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

Example 1:

Input: nums = [1,2,3,4]
Output: [24,12,8,6]

Example 2:

Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]

## Code:

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        left = [1 for _ in range(len(nums))]
        right = 1

        for i in range(len(nums)):
            if i == 0:
                ans[i] = 1
            else:
                ans[i] = ans[i-1] * nums[i-1]

        for j in range(len(nums)-1, -1, -1):
            if j == len(nums)-1:
                right = 1
            else:
                right *= nums[j+1]
                ans[j] *= right
                
        return ans
```
