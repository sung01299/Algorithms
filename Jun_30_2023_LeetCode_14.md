# 14. Longest Common Prefix

**Difficulty: Easy**

*Related Topics: String, Trie*

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"

Example 2:

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.

## Code:

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        ans=""
        strs = sorted(strs)
        first = strs[0]
        last = strs[-1]
        for i in range(min(len(first), len(last))):
            if (first[i]) != last[i]:
                return ans
            ans += first[i]
        return ans
```
