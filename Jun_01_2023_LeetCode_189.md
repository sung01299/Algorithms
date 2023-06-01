# 189. Rotate Array

**Difficulty: Medium**

*Related Topics: Array, Math, Two Pointers*

Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.

Example 1:

Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]

Example 2:

Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]

## Code:

```python
class Solution:
    class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        # Brute Force Code
        # rot = k % len(nums)
        # i = 0
        # for i in range(rot):
        #     curr = nums[-1]
        #     nums.pop()
        #     nums.insert(0, curr)
        
        # Two Pointers Algorithms
        # Reverse first half (0 ~ 'rot'), second half separately('rot' ~ end), and reverse the whole array at the end.
        def reverse(nums, i, j):
            while i < j:
                nums[i], nums[j] = nums[j], nums[i]
                i += 1
                j -= 1

        k %= len(nums)
        reverse(nums, 0, len(nums)-k-1)
        reverse(nums, len(nums)- k, len(nums)-1)
        reverse(nums, 0, len(nums)-1)
```
