# 22. Generate Parentheses

**Difficulty: Medium** 

*Related Topics: String, Dynamic Programming, Backtracking*

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

Example 1:

Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]

Example 2:

Input: n = 1
Output: ["()"]

## Code:

```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        stack = []
        res = []

        def backtrack(opened, closed):
            if opened == closed == n:
                res.append("".join(stack))
                return

            if opened < n:
                stack.append("(")
                backtrack(opened+1, closed)
                stack.pop()

            if opened > closed:
                stack.append(")")
                backtrack(opened, closed+1)
                stack.pop()
        backtrack(0, 0)
        return res
```
