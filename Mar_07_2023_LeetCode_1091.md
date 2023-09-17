# 1091. Shortest Path in Binary Matrix

## Related Topics: Array, BFS, Matrix

Given an n x n binary matrix grid, return the length of the shortest clear path in the matrix. If there is no clear path, return -1.

A clear path in a binary matrix is a path from the top-left cell (i.e., (0, 0)) to the bottom-right cell (i.e., (n - 1, n - 1)) such that:

All the visited cells of the path are 0.
All the adjacent cells of the path are 8-directionally connected (i.e., they are different and they share an edge or a corner).
The length of a clear path is the number of visited cells of this path.

 
Example 1:

Input: grid = [[0,1],[1,0]]
Output: 2

Example 2:

Input: grid = [[0,0,0],[1,1,0],[1,1,0]]
Output: 4

Example 3:

Input: grid = [[1,0,0],[1,1,0],[1,1,0]]
Output: -1

First Attempt:

Code:
```python
from collections import deque

class Solution:
    def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
        directions = ((-1,0),(1,0),(0,-1),(0,1),(-1,-1),(-1,1),(1,-1),(1,1))
        row = len(grid)
        col = len(grid[0])
        if grid[0][0] == 1:
            return -1
        def bfs(srow, scol):
            visited = [[False for i in range(col)] for _ in range(row)]
            count = 0
            visited[srow][scol] = True
            myque = deque()
            myque.append((srow, scol, count))
            while myque:
                curr = myque.popleft()
                visited[curr[0]][curr[1]] = True
                if curr[0] == row-1 and curr[1] == col-1:
                    return curr[2]+1
                for i in range(8):
                    nrow = curr[0] + directions[i][0]
                    ncol = curr[1] + directions[i][1]
                    if nrow < 0 or nrow > row-1 or ncol < 0 or ncol > col-1:
                        continue
                    if visited[nrow][ncol] == True:
                        continue
                    if grid[nrow][ncol] == 1:
                        continue           
                    myque.append((nrow, ncol, curr[2]+1))
                    visited[nrow][ncol] = True
            return -1

        return bfs(0,0)
```                 
