# 746. Longest Repeating Character Replacement

**Difficulty: Medium** 

*Related Topics: Hash Table, String, Sliding Window*

You are given a string s and an integer k. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most k times.

Return the length of the longest substring containing the same letter you can get after performing the above operations.

Example 1:

Input: s = "ABAB", k = 2
Output: 4
Explanation: Replace the two 'A's with two 'B's or vice versa.
Example 2:

Input: s = "AABABBA", k = 1
Output: 4
Explanation: Replace the one 'A' in the middle with 'B' and form "AABBBBA".
The substring "BBBB" has the longest repeating letters, which is 4.
There may exists other ways to achive this answer too.

## Code:

```python
from collections import Counter
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        ptr1, ptr2 = 0, 0
        ans = 0
        while ptr2 < len(s):
            word = s[ptr1:ptr2+1]
            count = Counter(word)
            if ptr2-ptr1+1 - count[max(count, key=count.get)] <= k:
                ans = max(ans, ptr2-ptr1+1)
                ptr2 += 1
            else:
                ptr1 += 1
                ptr2 = ptr1 + ans - 1
        
        return ans
```
