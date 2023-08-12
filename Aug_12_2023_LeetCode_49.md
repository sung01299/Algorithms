# 162. Group Anagrams

**Difficulty: Medium**

*Related Topics: Array, Hash Table, Sorting, String*

Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

Example 1:

Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]

Example 2:

Input: strs = [""]
Output: [[""]]

Example 3:

Input: strs = ["a"]
Output: [["a"]]

## Code:

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        c = {}

        for i in strs:
            if str(sorted(i)) not in c:
                c[str(sorted(i))] = [i]
            else:
                c[str(sorted(i))].append(i)
        
        return c.values()
```

