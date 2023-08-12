# 100. Same Tree

**Difficulty: Easy**

*Related Topics: Tree, Binary Tree, BFS, DFS*

Given the roots of two binary trees p and q, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

Example 1:

Input: p = [1,2,3], q = [1,2,3]
Output: true

Example 2:

Input: p = [1,2], q = [1,null,2]
Output: false

Example 3:

Input: p = [1,2,1], q = [1,1,2]
Output: false

## Code 1: DFS Solution

```python
class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        lstack = [p]
        rstack = [q]
        if p is None and q is None: return True
        elif (p and q is None) or (p is None and q): return False
        while lstack and rstack:
            l = lstack.pop()
            r = rstack.pop()
            if l.val != r.val: return False
            if l.left and r.left:
                lstack.append(l.left)
                rstack.append(r.left)
            elif (l.left and not r.left) or (not l.left and r.left): return False
            if l.right and r.right:
                lstack.append(l.right)
                rstack.append(r.right)
            elif (l.right and not r.right) or (not l.right and r.right): return False
        return True
```

## Code 2: Recursive Solution

```python
class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        if p is None and q is None: return True
        elif (p and q is None) or (p is None and q): return False
        if p.val == q.val:
            return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
