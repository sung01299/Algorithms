# 896. Monotonic Array

**Difficulty: Easy**

*Related Topics: Array*

An array is monotonic if it is either monotone increasing or monotone decreasing.

An array nums is monotone increasing if for all i <= j, nums[i] <= nums[j]. An array nums is monotone decreasing if for all i <= j, nums[i] >= nums[j].

Given an integer array nums, return true if the given array is monotonic, or false otherwise.

Example 1:

Input: nums = [1,2,2,3]
Output: true

Example 2:

Input: nums = [6,5,4,4]
Output: true

Example 3:

Input: nums = [1,3,2]
Output: false

## Code:

```python
class Solution:
    def isMonotonic(self, nums: List[int]) -> bool:
        if len(nums) == 1:
            return True
        if nums[0] > nums[-1]:
            for i in range(0, len(nums)-1):
                if nums[i] >= nums[i+1]:
                    continue
                else:
                    return False
            return True
        elif nums[0] < nums[-1]:
            for i in range(0, len(nums)-1):
                if nums[i+1] >= nums[i]:
                    continue
                else:
                    return False
            return True
        else:
            for i in range(1, len(nums)-2):
                if nums[i] != nums[0]:
                    return False
            return True
```
