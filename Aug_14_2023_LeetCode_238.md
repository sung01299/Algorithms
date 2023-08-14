# Product Of Array Except Self

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

## Code 1: Brute Force Solution Memory O(N)

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        left = [1 for _ in range(len(nums))]
        right = [1 for _ in range(len(nums))]

        for i in range(len(left)):
            if i == 0: left[i] = 1
            elif i == 1: left[i] = nums[0]
            else:
                left[i] = left[i-1] * nums[i-1]
        
        for j in range(len(right)-1, -1, -1):
            if j == len(right) - 1: right[j] = 1
            elif j == len(right) - 2: right[j] = nums[-1]
            else:
                right[j] = right[j+1] * nums[j+1]
        
        ans = []
        for i in range(len(nums)):
            ans.append(left[i] * right[i])
```

## Code 2: Prefix Sum Solution Memory O(1)
```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        ans = [1 for _ in range(len(nums))]
        for i in range(1, len(nums)):
            if i == 1: ans[i] = nums[i-1]
            else: ans[i] = ans[i-1] * nums[i-1]

        post = 1
        for i in range(len(nums)-2, -1, -1):
            post *= nums[i+1]
            ans[i] *= post
        return ans
```
