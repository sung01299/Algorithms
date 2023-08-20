# 74. Search A 2D Matrix

**Difficulty: Medium** 

*Related Topics: Array, Binary Search, Matrix*

You are given an m x n integer matrix matrix with the following two properties:

Each row is sorted in non-decreasing order.
The first integer of each row is greater than the last integer of the previous row.
Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m * n)) time complexity.

Example 1:

Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
Output: true

Example 2:

Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
Output: false

## Code:

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        def binary(l, r, nums, target):
            while l <= r:
                mid = (l + r) // 2
                if nums[mid] == target: return True
                elif nums[mid] < target: l = mid + 1
                else: r = mid - 1
            return False
        
        l = 0
        r = len(matrix) - 1
        while l <= r:
            mid = (l + r) // 2
            if matrix[mid][0] <= target and matrix[mid][-1] >= target:
                return binary(0, len(matrix[mid]), matrix[mid], target)
            elif matrix[mid][0] > target: r = mid-1
            elif matrix[mid][-1] < target: l = mid+1
        return False
```
