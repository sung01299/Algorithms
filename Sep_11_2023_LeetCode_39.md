# 46. Permutations

**Difficulty: Medium** 

*Related Topics: Array, Backtracking*

Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

Example 1:

Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

Example 2:

Input: nums = [0,1]
Output: [[0,1],[1,0]]

Example 3:

Input: nums = [1]
Output: [[1]]

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
