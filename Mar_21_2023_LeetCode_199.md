# 199. Binary Tree Right Side View

**Difficulty: Medium**

*Related Topics: Tree, BFS/DFS, Binary Tree*

Given the root of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

Example 1:

Input: root = [1,2,3,null,5,null,4]
Output: [1,3,4]

Example 2:

Input: root = [1,null,3]
Output: [1,3]

Example 3:

Input: root = []
Output: []

## Code:
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
from collections import deque
class Solution:
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        mydict = {}
        myq = deque()
        myq.append((root, 0))
        while myq:
            curr, lvl = myq.popleft()
            if curr:
                mydict[lvl] = curr.val
                if curr.left:
                    myq.append((curr.left, lvl+1))
                if curr.right:
                    myq.append((curr.right, lvl+1))

        return [mydict[i] for i in mydict]
```     
## Feedbacks: 
I traversed through the tree using Breadth-first search by levels. I constructed a dictionary to keep update the values of nodes as while loop
traverse through the tree. So, for each level, the right most node will be the last one to be updated in the dictionary for each levels. So, after the
while loop, I can get the right most value by each level.
