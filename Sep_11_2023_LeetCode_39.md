# 39. Combination Sum

**Difficulty: Medium** 

*Related Topics: Array, Backtracking*

Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.
The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.
The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.
 
Example 1:

Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.

Example 2:

Input: candidates = [2,3,5], target = 8
Output: [[2,2,2,2],[2,3,3],[3,5]]

Example 3:

Input: candidates = [2], target = 1
Output: []

## Code 1:

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        n = len(candidates)

        def backTracking(num, tmp):
            if num == target:
                res.append(sorted(tmp[:]))
                return
            elif num > target:
                return

            for i in range(n):
                if num + candidates[i] <= target:
                    tmp.append(candidates[i])
                    backTracking(num + candidates[i], tmp)
                    tmp.pop()
        backTracking(0, [])

        ans = []
        for elem in res:
            if elem not in ans:
                ans.append(elem)
        return ans
```

## Code 2:

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        n = len(candidates)
        """
        Decison Tree:
        Divide into two: Containing candidates[i], Not Containing candidates[i]
        """

        ans = []
        for elem in res:
            if elem not in ans:
                ans.append(elem)
        return ans

        def backTracking(i, cur, tmp):
            if cur == target:
                res.append(tmp[:])
                return
            if i >= n or cur > target:
                return
            
            # Divide into two branches
            tmp.append(candidates[i])
            backTracking(i, cur + candidates[i], tmp)
            tmp.pop()
            backTracking(i+1, cur, tmp)
        
        backTracking(0, 0, [])
        return res
```
