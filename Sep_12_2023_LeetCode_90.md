# 90. Subset II

**Difficulty: Medium** 

*Related Topics: Array, Backtracking, Bit Manipulation*

Given an integer array nums that may contain duplicates, return all possible 
subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

Example 1:

Input: nums = [1,2,2]
Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]

Example 2:

Input: nums = [0]
Output: [[],[0]]

## Code 1:

```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort()

        def backtrack(num, tmp):
            if num == k:
                res.append(tmp[:])
                return
            
            for i in range(num, len(nums)):
                tmp.append(nums[i])
                backtrack(i+1, tmp)
                tmp.pop()
        
        for k in range(len(nums)+1):
            backtrack(0, [])

        ans = []
        for elem in res:
            if elem not in ans:
                ans.append(elem)
        return ans
```

## Code 2:

```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort()

        def backtrack(ind, tmp):
            if ind == len(nums):
                res.append(tmp[:])
                return
            
            # All subsets that include nums[ind]
            tmp.append(nums[ind])
            backtrack(ind + 1, tmp)
            tmp.pop()
            # All subsets that don't include nums[ind]
            while ind + 1 < len(nums) and nums[ind] == nums[ind+1]:
                ind += 1
            backtrack(ind + 1, tmp)
        
        backtrack(0, [])
        return res
```
