# 78. Subsets

**Difficulty: Medium** 

*Related Topics: Array, Backtracking, Bit Manipulation*

Given an integer array nums of unique elements, return all possible 
subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

Example 1:

Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]

Example 2:

Input: nums = [0]
Output: [[],[0]]

## Code:

```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        def backtrack(ind, tmp):
            if len(tmp) == k:
                res.append(tmp[:])
                return
            
            for i in range(ind, n):
                tmp.append(nums[i])
                backtrack(i + 1, tmp)
                tmp.pop()

        res = []
        n = len(nums)
        for k in range(n+1):
            backtrack(0, [])
        return res
```
